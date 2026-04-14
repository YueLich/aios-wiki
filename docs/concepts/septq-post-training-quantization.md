---
type: concept
tags: [quantization, llm, post-training, on-device, model-compression, 优化技术]
related:
  - "[[quantization]]"
  - "[[on-device-llm]]"
  - "[[llama-cpp]]"
  - "[[mnn]]"
sources:
  - url: https://arxiv.org/abs/2604.10091
    title: "SEPTQ: A Simple and Effective Post-Training Quantization Paradigm for Large Language Models"
    date: 2026-04-14
created: 2026-04-14
---

# SEPTQ: 简单高效的 LLM 后训练量化范式

## 概述

SEPTQ 是一种新的 Post-Training Quantization (PTQ) 方法，旨在解决现有 PTQ 方法的两个痛点：

1. **复杂计算流程**：现有方法依赖复杂的校准和优化过程
2. **低比特退化严重**：在 INT4/INT2 等低位宽下性能大幅下降

## 量化方法对比

| 方法 | 额外训练 | 计算复杂度 | 低比特质量 |
|------|---------|-----------|-----------|
| QAT（量化感知训练） | 需要 | 高 | 好 |
| 传统 PTQ | 不需要 | 中 | 一般 |
| **SEPTQ** | **不需要** | **低** | **较好** |

## 为什么重要

端侧 LLM 部署的核心挑战之一是模型大小。SEPTQ 的价值在于：

- **简化部署流程**：无需复杂校准，降低 [[on-device-llm]] 的部署门槛
- **更低比特可用**：使 INT2/INT3 量化在移动端成为可能，进一步压缩模型体积
- **与现有工具链兼容**：可集成到 [[llama-cpp]]、[[mnn]] 等端侧推理框架

对于 [[mobile-ai-agent]] 场景，更激进的量化意味着可以运行更大的模型或在相同硬件上获得更快的响应。

## 相关技术

- [[quantization]] — 量化技术总览
- [[on-device-llm]] — 端侧 LLM 部署
- [[llama-cpp]] — llama.cpp 量化支持
- [[mnn]] — 阿里 MNN 推理引擎
