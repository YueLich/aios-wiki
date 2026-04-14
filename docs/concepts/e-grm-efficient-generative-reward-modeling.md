---
type: concept
tags: [llm, reward-model, inference-efficiency, on-device, quantization]
related:
  - "[[llm-inference]]"
  - "[[quantization]]"
  - "[[on-device-llm]]"
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

对于 [[on-device-llm]] 和 [[edge-inference]] 场景，推理效率是核心瓶颈。E-GRM 的"按需推理"策略可以：
- 减少端侧 LLM 的平均推理延迟
- 降低移动端设备的能耗
- 为 [[ai-agent]] 在手机上的实时交互提供更好的用户体验

这与 [[quantization]] 等模型压缩技术形成互补——前者减少计算量，后者减少模型大小。

## 相关技术

- [[llm-inference]] — 推理优化
- [[quantization]] — 模型压缩
- [[on-device-llm]] — 端侧部署
