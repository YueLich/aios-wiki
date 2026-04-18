---
type: concept
tags: [llm, reward-model, inference-efficiency, on-device, quantization]
related:
  - "[[on-device-inference-memory-pressure]]"
  - "[[septq-post-training-quantization]]"
  - "[[septq-post-training-quantization]]"
sources:
  - url: https://arxiv.org/abs/2604.10072
    title: "Reason Only When Needed: Efficient Generative Reward Modeling via Model-Internal Uncertainty"
    date: 2026-04-14
created: 2026-04-14
---

# E-GRM: Efficient Generative Reward Modeling

## 概述

E-GRM 是一种基于模型内部不确定性的高效生成式奖励建模框架。它解决了现有 Generative Reward Model (GRM) 的两个关键问题：

1. **过度推理**：现有 GRM 对所有输入无差别应用 Chain-of-Thought 推理，即使简单任务也产生不必要的计算开销
2. **评估粒度不足**：投票机制无法精确评估推理质量

## 核心思想

E-GRM 通过监控模型内部的收敛行为来判断何时需要 CoT 推理：
- **简单输入**：模型内部状态快速收敛 → 跳过 CoT，直接推理
- **复杂输入**：内部状态不确定 → 触发 CoT 推理

## 为什么重要

对于 [[septq-post-training-quantization]] 和 [[on-device-inference-memory-pressure]] 场景，推理效率是核心瓶颈。E-GRM 的"按需推理"策略可以：
- 减少端侧 LLM 的平均推理延迟
- 降低移动端设备的能耗
- 为  在手机上的实时交互提供更好的用户体验

这与 [[septq-post-training-quantization]] 等模型压缩技术形成互补——前者减少计算量，后者减少模型大小。

## 相关技术

- [[on-device-inference-memory-pressure]] — 推理优化
- [[septq-post-training-quantization]] — 模型压缩
- [[septq-post-training-quantization]] — 端侧部署

## 核心问题

We describe KVLink, an approach for efficient key-value (KV) cache reuse in large language models (LLMs). In many LLM applications, different inputs can share overlapping context, such as the same retrieved document appearing in multiple queries. However, the LLMs still need to encode the entire context for each query, leading to redundant computation. In this paper, we investigate a new strategy to eliminate such inefficiency, where the KV cache of each document is precomputed independently. During inference, the KV caches of retrieved documents are concatenated, allowing the model to reuse cached representations instead of recomputing them. To mitigate the performance degradation when using KV caches computed independently for each document, KVLink introduces two key techniques: adjustin

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[mnn-350]] — 推理引擎
- [[kv-cache-quantization-ondevice]] — 内存优化
