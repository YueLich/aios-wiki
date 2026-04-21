---
type: entity
tags: [推理引擎, Apple Silicon, MLX, LLM, 基准测试]
related: [[ggml-llamacpp-hf]], [[coremltools-9]], [[imp-mobile-lmm]]
sources:
  - url: https://arxiv.org/abs/2511.05502
    title: "Production-Grade Local LLM Inference on Apple Silicon: A Comparative Study of MLX, MLC-LLM, Ollama, llama.cpp, and PyTorch MPS"
    date: 2025-11-08
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Apple Silicon 本地 LLM 推理全面对比

> 在 Apple M2 Ultra (192GB 统一内存) 上，对 MLX、MLC-LLM、Ollama、llama.cpp、PyTorch MPS 五大本地 LLM 运行时进行了系统性实证评估，使用 Qwen-2.5 模型家族在 100 至 100K token 的 prompt 范围内测量各项性能指标。

## 核心问题

Apple Silicon 的统一内存架构为端侧 LLM 推理提供了独特优势（大内存容量、高带宽、CPU/GPU 共享），但目前存在多个竞争运行时（MLX、MLC-LLM、Ollama、llama.cpp、PyTorch MPS），开发者缺乏系统性的性能对比数据来指导选择。

## 方法/架构

- **测试平台**：Mac Studio，M2 Ultra 处理器，192GB 统一内存
- **模型**：Qwen-2.5 模型家族（多个参数规模）
- **Prompt 范围**：从几百 token 到 100K token
- **测量指标**：Time-to-First-Token (TTFT)、吞吐量、内存使用等

## 实验结果

| 运行时 | 优势场景 | 关键指标 |
|--------|---------|---------|
| MLX | Apple 原生优化，大模型推理 | 统一内存利用率高 |
| MLC-LLM | 跨平台部署，模型编译优化 | 首次 token 延迟低 |
| Ollama | 易用性最佳，开箱即用 | 用户体验友好 |
| llama.cpp | 生态最广，量化支持最强 | 小模型效率高 |
| PyTorch MPS | 研究灵活性，自定义能力强 | 适合实验开发 |

## 关键洞察

**统一内存是 Apple 推理的核心优势**：192GB 统一内存允许运行超大模型而无需量化，这是 x86 平台无法比拟的。但不同运行时对统一内存的利用率差异显著。

**没有"最佳"运行时**：不同运行时在不同场景（小 prompt vs 大 prompt、小模型 vs 大模型、批量推理 vs 交互式推理）下各有优劣。选择应基于具体使用场景。

## 为什么重要

- **iPhone/Mac AI 开发者指南**：为 Apple 生态下的端侧 LLM 推理选型提供了最全面的基准数据
- **统一内存架构的潜力**：展示了 Apple Silicon 在端侧 AI 推理方面的独特优势
- **运行时生态成熟度**：揭示了各运行时的实际表现和适用场景

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 是评测对象之一，该页面详细介绍了其架构和优化技术
- [[coremltools-9]] — Apple 的模型转换工具链，与这些运行时协同工作
- [[imp-mobile-multimodal]] — 另一个端侧多模态模型，可在 Apple Silicon 上部署
