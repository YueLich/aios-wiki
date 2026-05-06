---
title: "PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning"
arXiv: 2605.01061
date: 2026-05-01
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning

**作者:** Beining Wu, Zihao Ding, Jun Huang
**发表:** 2026-05-01

## 摘要

While current federated multimodal continual learning over mixture-of-experts low-rank adaptation (MoE-LoRA) is built on the unverified assumption that routing isolates task-specific knowledge into disjoint experts, we argue that routing operates per-sample, while forgetting accumulates across the task sequence, and gradient conflict persists within each expert even when routing is maximally polarized. Moreover, activation-subspace protection can also fail because, under parameter-efficient fine-tuning, it entangles tasks due to a dimension-counting bound, and federated averaging (FedAvg) disrupts client-side orthogonality. To address this, we propose PRISM (Per-expert Routing-projection Interference-informed Subspace Method), which maintains a per-expert gradient subspace basis whose orthogonality is preserved under FedAvg and reinterprets MoE routing as a capacity allocator.

## 核心贡献

1. **问题暴露**: 首次系统揭示了 MoE-LoRA 路由假设中的"伪隔离"问题——路由逐样本操作，而遗忘跨任务累积，梯度冲突在每个 expert 内部持续存在
2. **FedAvg 正交性破坏**: 证明联邦平均会破坏客户端正交性，激活子空间保护在参数高效微调下会因维度计数约束而失效
3. **PRISM 方法**: 维护 per-expert 梯度子空间基，其正交性在 FedAvg 下得以保持，并将 MoE 路由重新解释为容量分配器
4. **SOTA 性能**: 在 LLaVA-1.5-7B/13B 和 Qwen2.5-VL-7B 上，在 CoIN-6 和 CoIN-Long-10 上超越 16 个 state-of-the-art 基线

## 为什么重要

首个深入分析联邦多模态持续学习中路由伪隔离问题的工作。发现现有方法依赖的"路由隔离假设"在实际场景中不成立，导致任务知识并非真正独立存储在各自 expert 中。这一发现对设计更可靠的联邦持续学习系统有重要指导意义。

## 与端侧/移动端的相关性

联邦学习本身就是为了保护用户隐私的分布式学习范式，与端侧部署高度相关。PRISM 对 MoE 路由的重新解释（容量分配而非任务隔离）和梯度子空间正交性保持，对在移动设备上运行联邦多模态持续学习系统有直接价值。
