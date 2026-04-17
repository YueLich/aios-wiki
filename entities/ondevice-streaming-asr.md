---
type: entity
tags: [asr, on-device, quantization, onnx, edge-inference, microsoft, streaming]
related: [[edgeflow-cold-start]], [[septq-post-training-quantization]], [[kv-cache-quantization-ondevice]], [[kl-quantization-ssm-transformer]], [[fastshade-mobile-denoising]]
sources:
  - url: https://arxiv.org/abs/2604.14493
    title: "Pushing the Limits of On-Device Streaming ASR: A Compact, High-Accuracy English Model for Low-Latency Inference"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# On-Device Streaming ASR

> 微软 CoreAI 团队的端侧流式 ASR 系统研究：在 CPU 上实现 8.20% WER、0.56s 延迟、0.67GB 模型大小，建立了端侧语音识别的质量-效率帕累托前沿。

## 核心问题

高质量 ASR 模型（Qwen3-ASR-1.7B 5.90% WER、Parakeet TDT-0.6B-v3 6.32%、Canary-1B-v2 7.15%）都是批处理架构，需要 2-7GB 内存和 GPU 推理。端侧部署面临四大约束：
1. **流式能力**：必须以亚秒延迟处理音频块
2. **高精度**：跨多种英语场景的 WER 需有竞争力
3. **最少资源**：模型需在 1GB 以内，CPU 上运行速度快于实时
4. **纯 CPU 推理**：无 GPU 加速

## 方法/架构

### 系统架构
基于 **NVIDIA Nemotron Speech Streaming** 模型（0.6B 参数），通过 **ONNX Runtime** 实现完整推理流水线。

### 评估范围
系统性评估了 50+ 种配置，涵盖：
- **架构范式**：Encoder-Decoder、Transducer、LLM-based
- **推理模式**：批处理、分块、流式
- **模型**：Whisper、Nemotron、Parakeet TDT、Canary、Conformer Transducer、Qwen3-ASR

### 量化策略
对最佳候选模型（Nemotron 0.6B）应用多种后训练量化：
- **Importance-weighted k-quant**：按权重重要性分配不同位宽
- **混合精度方案**：关键层保留高精度，非关键层压缩
- **Round-to-nearest (RTN)**：标准量化基线
- **图级算子融合**：优化 ONNX 计算图

### 流式配置
使用配置元组 `(chunk_size, history, lookahead)` 控制流式行为：
- 推荐配置：`(7, 10, 7)` — 0.56s 算法延迟，5.6s 历史窗口
- 超低延迟配置：`(2, 20, 2)` — 0.16s 算法延迟

## 实验结果

### 评估基准
8 个标准英语 ASR 数据集（ESB 套件）：AMI（会议）、Earnings22（财报电话）、GigaSpeech（互联网音频）、LibriSpeech Clean/Other（有声书）、SPGISpeech（金融转录）、TED-LIUM（演讲）、VoxPopuli（欧洲议会）。

### Nemotron 0.6B ONNX 量化结果

| 配置 | 格式 | 大小 | 设备 | 平均 RTFx | 平均 WER |
|------|------|------|------|----------|---------|
| PyTorch 基线 | PyTorch | 2.47 GB | CUDA | 7.28 | — |
| FP32 ONNX | ONNX | 2.47 GB | CPU | 8.03 | — |
| int8 k-quant | ONNX | 1.28 GB | CPU | 8.01 | — |
| int4-mixed k-quant | ONNX | 0.73 GB | CPU | 8.12 | — |
| **int4 k-quant (推荐)** | **ONNX** | **0.67 GB** | **CPU** | **8.20** | — |
| int4 RTN | ONNX | 0.66 GB | CPU | 8.46 | — |

### 核心数据
- **推荐配置（int4 k-quant）**：0.67 GB、8.20% 平均 WER、0.56s 算法延迟
- **WER 退化**：仅 1% 绝对值（相对于 PyTorch 全精度基线）
- **模型压缩**：从 2.47 GB 压缩至 0.67 GB（73% 减少）
- **超低延迟配置**：0.16s 算法延迟，8.89% WER

### 各数据集详细 WER（int4 k-quant, 0.56s 延迟）
- AMI: 7.20% | Earnings22: 17.05% | GigaSpeech: 13.60%
- LibriSpeech Clean: 12.10% | LibriSpeech Other: 2.38%
- SPGISpeech: 5.04% | TED-LIUM: 2.83% | VoxPopuli: 7.98%

## 关键洞察

1. **Nemotron Streaming > 所有其他架构**：在流式场景下，Nemotron Speech Streaming 优于 Whisper、Qwen3-ASR 等更大模型。证明了专用流式架构的价值。

2. **k-quant 优于 RTN**：重要性加权的 k-quant 在相同大小下比 round-to-nearest 保持更低 WER，验证了按权重重要性分配位宽的有效性。

3. **1GB 以内的端侧 ASR 可行**：0.67 GB + CPU 推理 + 8.20% WER + 0.56s 延迟，四个约束同时满足，建立了端侧流式 ASR 的新帕累托前沿。

4. **超低延迟的代价可控**：0.16s 延迟配置仅将 WER 从 8.20% 增加到 8.89%，适合对延迟极度敏感的场景（实时字幕、语音控制）。

## 为什么重要

这项工作直接回答了"端侧能否运行高质量 ASR"的问题：**可以**。0.67GB 的模型在纯 CPU 上以 8.20% WER 实时运行，对以下场景有直接影响：
- 手机端实时字幕和语音转文本
- 车载语音助手（离线模式）
- IoT 设备的语音唤醒与指令识别
- 隐私敏感场景的本地语音处理

ONNX Runtime 方案使模型可跨平台部署（iOS、Android、Linux、Windows），降低了端侧 ASR 的工程门槛。

## 关联
- [[edgeflow-cold-start]] — EdgeFlow 优化 LLM 冷启动，本工作优化 ASR 冷启动/流式延迟
- [[septq-post-training-quantization]] — SEPTQ 量化范式，本工作使用类似的 k-quant 策略
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，本工作是模型权重量化
- [[kl-quantization-ssm-transformer]] — KL 敏感度量化，本工作按权重重要性量化
- [[fastshade-mobile-denoising]] — FastSHADE 端侧推理优化，同属端侧高效推理领域
