---
type: entity
tags: [推理框架, Apple Silicon, MLX, llama.cpp, 推理优化, 多模态]
related: [[ggml-llamacpp-hf]], [[coremltools-9]], [[litertlm-swift-ios]], [[gemma4-ondevice]]
sources:
  - url: https://arxiv.org/abs/2601.19139
    title: "Native LLM and MLLM Inference at Scale on Apple Silicon"
    date: 2026-01-31
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# vllm-mlx: Apple Silicon 原生 LLM/MLLM 推理框架

> 基于 MLX 的端侧大模型推理框架，在 Apple M4 Max 上实现 525 tok/s 吞吐，比 llama.cpp 快 21%-87%。开源实现。

## 核心问题

Apple Silicon 的统一内存架构（最高 192GB 共享 CPU/GPU 内存，400+ GB/s 带宽）为端侧推理提供了天然优势。但现有工具要么缺乏原生优化（PyTorch MPS 只是适配 CUDA 风格），要么只支持文本模型，多模态工作负载严重不足。

## 方法/架构

vllm-mlx 基于 Apple MLX 框架构建，实现了三个核心创新：

### 1. 文本推理：连续批处理 + 原生 MLX 优化
- **连续批处理（Continuous Batching）**：在 16 并发请求时实现 4.3x 聚合吞吐扩展
- **MLX 原生优势**：真正的零拷贝操作利用统一内存、惰性求值融合操作减少内存分配开销、原生量化支持高效反量化核
- 覆盖模型：Qwen3（0.6B-72B）、Llama 3、Gemma 3、GLM-4、Nemotron-30B

### 2. 多模态推理：基于内容的前缀缓存
- **内容哈希去重**：通过内容哈希识别相同图像，无论输入格式如何
- 消除冗余视觉编码：相同图像（或视频帧）不再重复处理
- 视频分析（64 帧）：24.7x 缓存加速

### 3. 与 llama.cpp 的差异定位
- llama.cpp：基于 GGML，CPU/GPU 混合，量化出色但批处理弱
- vllm-mlx：MLX 原生，统一内存零拷贝，连续批处理 + 前缀缓存
- 两者互补：llama.cpp 适合超低延迟单请求；vllm-mlx 适合多并发 + 多模态场景

## 实验结果

在 Apple M4 Max 128GB 上的评估：

| 指标 | vllm-mlx | llama.cpp | 提升 |
|------|----------|-----------|------|
| 文本吞吐 | 最高 525 tok/s | 基准 | +21% ~ +87% |
| 并发扩展 | 4.3x @16请求 | 无连续批处理 | — |
| 重复图像查询延迟 | <1s | 21.7s | 28x 加速 |
| 视频分析（64帧） | — | — | 24.7x 缓存加速 |

## 关键洞察

1. **统一内存是端侧推理的关键差异化因素**：Apple Silicon 的统一内存架构让 MLX 可以实现真正的零拷贝，而 CUDA 生态的"统一内存"实际上是分层的。

2. **多模态前缀缓存是杀手特性**：在实际移动场景中（图片搜索、视频分析、屏幕理解），大量图像被重复处理。内容哈希去重将 21.7 秒延迟降至 1 秒以内。

3. **连续批处理填补了端侧空白**：传统端侧推理是"单请求"模式，4.3x 的并发扩展使端侧部署更具可行性。

## 为什么重要

vllm-mlx 证明了 Apple Silicon 不只是"能跑模型"，而是在特定场景下可以达到接近云端的推理体验。iPhone/iPad 的统一内存架构一致，因此类似提升适用于移动端。

## 关联
- [[ggml-llamacpp-hf]] — 主要竞品，两者定位互补
- [[coremltools-9]] — Apple 端侧工具链另一支柱
- [[litertlm-swift-ios]] — 另一个 iOS 端侧推理方案
- [[gemma4-ondevice]] — vllm-mlx 支持的关键模型
