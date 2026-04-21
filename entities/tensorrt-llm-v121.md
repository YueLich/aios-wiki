---
type: entity
tags: [inference, gpu, nvidia, tensorrt, quantization, 推理框架]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[vllm]], [[coremltools-9]]
sources:
  - url: https://github.com/NVIDIA/TensorRT-LLM/releases/tag/v1.2.1
    title: "NVIDIA/TensorRT-LLM v1.2.1"
    date: 2026-04-20
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# NVIDIA TensorRT-LLM v1.2.1

> NVIDIA 的高性能 LLM 推理优化引擎，v1.2.1 于 2026-04-20 发布，持续优化 GPU 上的 LLM 推理性能。虽然主要面向服务器端 GPU，但其优化技术对手机端推理引擎设计有参考价值。

## 概述

TensorRT-LLM 是 NVIDIA 基于 TensorRT 的 LLM 专用推理引擎，提供：
- **FP8/INT8/INT4 量化**：支持多种精度的模型压缩
- **PagedAttention**：高效的 KV-Cache 内存管理
- **连续批处理（Continuous Batching）**：动态调度请求以最大化 GPU 利用率
- **TensorRT 引擎编译**：将模型编译为高度优化的 GPU kernel 序列
- **多 GPU/多节点推理**：支持张量并行和流水线并行

## v1.2.1 变更

- 版本发布于 2026-04-20
- 作为补丁版本，包含稳定性修复和性能优化
- 详细变更日志需参考 GitHub release notes

## 为什么重要

虽然 TensorRT-LLM 主要面向 NVIDIA GPU 服务器，但它对手机端 AIOS 的价值体现在：
1. **优化技术借鉴**：PagedAttention、连续批处理等技术可以迁移到手机端推理引擎（如 MNN、llama.cpp）
2. **量化方法参考**：FP8/INT4 量化方案在端侧部署中有直接参考价值
3. **生态对比**：与 Apple CoreML、Qualcomm SNPE 等端侧推理方案形成技术竞争对比
4. **云端-端侧协同**：手机端 Agent 可以将重负载卸载到运行 TensorRT-LLM 的云端 GPU

## 关联

- [[ggml-llamacpp-hf]] — CPU/端侧推理引擎，与 TensorRT-LLM 形成互补
- [[mnn-350]] — 阿里 MNN 端侧推理框架
- [[vllm]] — 服务端 LLM 推理引擎，与 TensorRT-LLM 竞争
- [[coremltools-9]] — Apple 端侧推理工具链
