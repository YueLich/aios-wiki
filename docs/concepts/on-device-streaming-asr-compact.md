---
type: concept
tags: [asr, streaming, on-device, quantization, onnx, nemotron, edge-ai, 语音识别]
related: [[ondevice-streaming-asr]], [[kv-cache-quantization-ondevice]], [[edgeflow-cold-start]], [[coremltools-9]], [[mnn-350]]
sources:
  - url: https://arxiv.org/abs/2604.14493v1
    title: "Pushing the Limits of On-Device Streaming ASR: A Compact, High-Accuracy English Model for Low-Latency CPU Inference"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Pushing the Limits of On-Device Streaming ASR

> 系统性实证研究：在 CPU-only 条件下实现高精度流式语音识别，模型压缩至 0.67GB，WER 仅 8.20%（FP32 基线 8.03%），实时因子 >6×。

## 核心问题

端侧 ASR 部署面临三重矛盾：高精度模型（Qwen3-ASR-1.7B, Whisper Large-v3-Turbo）通常需要 2-7GB 内存和 GPU 加速，但边缘设备仅有 CPU 和有限内存预算。现有模型在批处理模式下表现优异（WER 5.90%-7.15%），但切换到流式模式后严重退化——Qwen3-ASR 从 5.90% 跳升至 10.45%（2.4s stride）。

## 方法/架构

### 评估模型矩阵（6 大系列，50+ 配置）

| 模型 | 架构 | 模式 | 大小 |
|------|------|------|------|
| Whisper Large-v3-Turbo | Encoder-Decoder | Batch | 1.62GB |
| Nemotron-0.6B | Cache-aware Transducer | Stream/Batch | 2.47GB |
| Parakeet TDT-0.6B-v3 | TDT Transducer | Chunk/Batch | 2.51GB |
| Canary-1B-v2 | AED + AlignAtt | Chunk/Batch | 6.36GB |
| Qwen3-ASR-1.7B | LLM-based ASR | Batch/Chunk | 4.70GB |

### 优化管线：Nemotron Speech → ONNX → 量化

最终方案基于 NVIDIA Nemotron Speech Streaming，通过 ONNX Runtime 部署：
- **缓存感知架构**：专为流式设计，batch→streaming 仅损失 0.21% WER
- **量化方案**：int4 k-quant 将模型从 2.47GB 压缩至 0.67GB（73% 压缩率）
- **算子融合**：ConvInt 进一步加速但 WER 升至 10.14%，不推荐
- **流式配置**：(7, 10, 7) = 0.56s 算法延迟，5.6s 历史窗口

## 实验结果/关键数据

### 量化 vs 精度（Nemotron-0.6B，CPU 推理）

| 量化方案 | 模型大小 | 平均 WER | RTFx | 相对退化 |
|----------|----------|----------|------|----------|
| FP32 (ONNX) | 2.47GB | 8.03% | 6.73× | 基线 |
| int8 k-quant | 1.28GB | 8.01% | 7.25× | -0.2% |
| int4-mixed | 0.73GB | 8.12% | 7.15× | +1.1% |
| **int4 k-quant** | **0.67GB** | **8.20%** | **7.20×** | **+2.1%** |
| int4 RTN | 0.66GB | 8.46% | 7.30× | +5.4% |

### 关键发现

1. **量化近乎无损**：int8 k-quant WER 8.01% vs FP32 8.03%，模型缩小 48%
2. **4-bit 压缩可行**：int4 仅 0.67GB，WER 仅升 0.17 个百分点（相对 2.1%）
3. **CPU 推理实用**：所有 ONNX 变体 RTFx > 6×（6 倍实时速度），首 token 延迟 < 0.7s
4. **离线精度≠流式精度**：批处理 WER 不能预测流式表现，必须单独评估
5. **历史窗口敏感**：5.6s 历史 vs 1.6s 历史，WER 差距 1.23%（7.28% vs 8.51%）

## 关键洞察

这篇论文的核心贡献不是单一模型，而是建立了一套**端侧 ASR 系统化评估方法论**。50+ 配置的对比揭示了几个反直觉结论：

- **Cache-aware Transducer 比 LLM-based ASR 更适合端侧**：Qwen3-ASR 虽然 batch WER 最低（5.90%），但流式退化严重，且需要 4.7GB。Nemotron 以 0.67GB 和最小退化胜出。
- **量化收益呈递减但可接受**：int4 比 int8 多压缩 48%（1.28→0.67GB），但 WER 仅升 0.19%，是端侧部署的甜蜜点。
- **算法延迟与精度的权衡**：0.56s 延迟要求 5.6s 历史窗口，这对内存有隐含成本，但在现代设备上完全可承受。

## 为什么重要

对手机端 AIOS 生态的意义：
- **语音助手本地化**：证明 0.67GB + CPU 即可实现高质量流式 ASR，使 Siri/AI 助手脱云成为现实
- **隐私保护**：纯端侧推理意味着语音数据无需上传
- **NPU 加速空间**：论文仅用 CPU 即达 RTFx 6×，若利用 NPU 可进一步降低功耗
- **[[ondevice-streaming-asr]] 作为技术参考**：为其他端侧模型（TTS、翻译）提供量化→ONNX→流式的标准管线

## 关联
- [[ondevice-streaming-asr]] — 同主题已有页面，本文为更系统的最新研究
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化与 ASR 量化技术互补
- [[edgeflow-cold-start]] — 冷启动优化可与流式 ASR 结合
- [[coremltools-9]] — Apple 端侧部署工具链，对比 ONNX Runtime 方案
- [[mnn-350]] — 阿里端侧推理引擎，可作为 ONNX 的替代部署后端
