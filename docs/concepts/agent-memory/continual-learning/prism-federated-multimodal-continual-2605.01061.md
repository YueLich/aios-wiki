---
title: "PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning"
arXiv: 2605.01061
date: 2026-05-01
tags: [agent-memory, continual-learning, federated-learning, multimodal]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **作者**: Beining Wu, Zihao Ding, Jun Huang
- **发表**: 2026-05-01
- **方向**: 持续学习 · 联邦学习 · 多模态

## 摘要（翻译）

当前基于 MoE-LoRA（Mixture-of-Experts 低秩适应）的联邦多模态持续学习建立在一个未验证的假设上：路由将任务特定知识隔离到不相交的专家中。本文论证：

- **路由是 per-sample 操作的**，而遗忘是跨任务序列累积的
- **每个专家内部也存在梯度冲突**，即使路由完全极化
- **激活子空间保护也可能失败**：在参数高效微调下，由于维度计数约束，任务会纠缠在一起
- **联邦平均（FedAvg）破坏了客户端正交性**

本文提出 **PRISM（Per-expert Routing-projection Interference-informed Subspace Method）**：
- 维护 per-expert 梯度子空间基，其正交性在 FedAvg 下得以保持
- 将 MoE 路由重新解释为容量分配器

在 LLaVA-1.5-7B、LLaVA-1.5-13B 和 Qwen2.5-VL-7B 上，PRISM 在 CoIN-6 和 CoIN-Long-10 上**超越 16 个 SOTA 基线**，平均准确率最优。

## 核心发现

| 对比项 | CoIN-6 | CoIN-Long-10 |
|--------|--------|-------------|
| 相对最佳联邦多模态基线 | +3.23 pp | +6.06 pp |

## 为什么重要

联邦多模态持续学习结合了两个现实挑战：
1. **隐私约束下的跨客户端知识聚合**
2. **多模态（文本+视觉）输入的持续适应**

PRISM 揭示了当前方法中基于路由隔离的假设存在根本性缺陷，并提出了有效的解决方案。

## 与移动端/端侧的相关性

移动端是联邦学习的天然场景：
- 用户数据不需要离开设备
- 多模态输入（视觉+语音+文本）在移动端丰富
- 端侧个性化适应与联邦学习天然结合

PRISM 的梯度子空间正交性保持方法对移动端的隐私保护学习有直接参考价值。

---

*注：本文为新发现论文（2605.01061）。*
