---
type: entity
tags: [ggml, llama.cpp, huggingface, local-ai, inference, infrastructure]
related: [[on-device-inference]], [[llama-cpp]], [[mnn]]
sources:
  - url: https://huggingface.co/blog/ggml-llamacpp-joins-hf
    title: "GGML and llama.cpp join HuggingFace to ensure long-term progress of Local AI"
    date: 2026-04
created: 2026-04-14
---

# GGML 与 llama.cpp 加入 HuggingFace

## 概述

GGML 和 llama.cpp 正式加入 HuggingFace，以确保本地 AI 推理工具的长期可持续发展。这是开源 AI 基础设施的重要里程碑。

## 为什么重要

**llama.cpp** 是端侧 LLM 推理的事实标准，支持 GGUF 格式和各种量化方案。加入 HuggingFace 意味着：
- **资源保障**：获得 HuggingFace 的资金和工程支持
- **生态整合**：与 HuggingFace Hub、Transformers 等深度集成
- **长期可持续**：解决了开源项目维护者 burnout 的风险

对 [[mobile-aios-overview]] 的影响：llama.cpp 是 [[on-device-inference]] 的核心技术栈之一，其稳定性直接关系到整个端侧 AI 生态。

## 关联

- [[mnn]] — 竞争/互补的推理框架
- [[gemma4-ondevice]] — 可用 llama.cpp 推理的模型
- [[edgeflow-cold-start]] — 推理优化技术
