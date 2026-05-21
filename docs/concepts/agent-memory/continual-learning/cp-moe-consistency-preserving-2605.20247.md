---
title: "CP-MoE: Consistency-Preserving Mixture-of-Experts for Continual Learning"
arXiv: "2605.20247"
date: "2026-05-18"
tags: [continual-learning, mixture-of-experts, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: CP-MoE: Consistency-Preserving Mixture-of-Experts for Continual Learning
- **arXiv ID**: 2605.20247
- **作者**: Yang Liu, Toan Nguyen, Flora D. Salim
- **发表日期**: 2026-05-18
- **方向**: Continual Learning / MoE

## 核心贡献

1. **解决 MoE 持续学习的核心矛盾**: 指出现有 LoRA-based MoE 持续学习方法面临知识隔离与迁移的两难——要么专家隔离过于激进，限制跨任务知识迁移；要么允许任务特定更新覆盖重要参数，导致严重遗忘。
2. **一致性保持机制**: 提出 CP-MoE，通过保持决策边界一致性来缓解专家扩张带来的路由漂移问题。
3. **参数高效与知识保留的平衡**: 在 LoRA 框架下实现 MoE 架构的持续学习，在参数效率与学习能力间取得更好平衡。

## 摘要

Catastrophic forgetting remains a major obstacle to continual learning in large language models (LLMs) and vision--language models (VLMs). Although Mixture-of-Experts (MoE) architectures offer an efficient path to scaling, existing LoRA-based MoE continual learning methods still face a fundamental trade-off: they either isolate experts too aggressively, limiting knowledge transfer across tasks, or allow task-specific updates to overwrite important existing parameters, leading to severe forgetting.

## 详细解读

### 研究背景

MoE 架构（如 Mixtral）在持续学习中展现出潜力——新增专家可以学习新任务而不干扰已有知识。但现有方法存在根本性两难：

- **过于激进的知识隔离**: 只让相关专家处理特定任务，虽然保护了旧知识，但限制了跨任务的泛化和知识迁移
- **参数覆盖问题**: 允许跨专家的参数更新，导致新任务的知识覆盖旧任务的专家参数

### 核心方法

CP-MoE 的设计：
- **一致性保持**: 当新增专家时，保持路由决策与之前的一致性分布，避免路由漂移
- **跨任务知识迁移**: 通过对比学习等机制，让新专家学习时能利用旧专家的知识
- **参数重要性正则化**: 对重要参数施加更大的更新惩罚，保护关键知识

## 为什么重要

这篇工作揭示了 MoE 持续学习中"隔离 vs 迁移"的核心矛盾，并提出了有效的解决思路。对边缘设备上的增量学习模型更新有直接意义。

## 与端侧/移动端的相关性

在移动端部署持续学习的 MoE 模型非常有价值：
- 可以在设备上增量学习用户特定知识
- 新增专家不需要重新训练整个模型
- 一致性保持机制可以减少本地微调时的灾难性遗忘

## 参考文献

（参考文献待从原文补充）
