---
type: entity
tags: [推理框架, llama.cpp, GitHub, GGML, 端侧推理]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8797]], [[mnn-350]], [[gemma-cpp-inference]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8808
    title: "ggml-org/llama.cpp: b8808"
    date: 2026-04-16
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# llama.cpp b8808

> GGML 生态的核心推理引擎持续迭代，b8808 是最新版本（2026-04-16 发布），包含多项推理优化和 bug 修复。

## 概述

llama.cpp 是端侧 LLM 推理的事实标准框架，基于 GGML 张量库，支持 CPU、Apple Silicon 和消费级 GPU 推理。b8808 继续在性能优化和模型兼容性方面推进。

## 版本追踪

| 版本 | 发布日期 | 距前版间隔 |
|------|----------|-----------|
| b8783 | 2026-04-08 | — |
| b8795 | 2026-04-13 | 5天 |
| b8797 | 2026-04-14 | 1天 |
| b8796 | 2026-04-14 | 同日 |
| **b8808** | **2026-04-16** | **2天** |

开发节奏非常快，几乎每日都有新版本发布。

## 端侧推理生态位置

llama.cpp 在手机端 AIOS 的推理栈中占据核心位置：

- **GGML 格式**是端侧模型分发的事实标准
- 支持多种量化方案 (Q4_0, Q4_1, Q5_0, Q5_1, Q8_0 等)
- 与 [[mnn-350]] (阿里 MNN) 和 CoreML 形成竞争/互补关系
- [[ggml-llamacpp-hf]] 与 HuggingFace 的整合加速了生态发展

## 关联

- [[ggml-llamacpp-hf]] — GGML/llama.cpp 加入 HuggingFace 的背景
- [[llamacpp-b8797]] — 前一版本
- [[mnn-350]] — 竞争推理框架
- [[gemma-cpp-inference]] — gemma.cpp 基于 GGML 库
- [[kl-quantization-ssm-transformer]] — 量化技术与 llama.cpp 的量化方案互补
