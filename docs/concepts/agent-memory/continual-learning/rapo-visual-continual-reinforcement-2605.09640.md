---
title: "Overcoming Catastrophic Forgetting in Visual Continual Learning with Reinforcement Fine-Tuning"
arXiv: 2605.09640
date: 2026-05-10
tags: [agent-memory, continual-learning, reinforcement-learning, visual]
reviewer: auto
source: arXiv API
---

# Overcoming Catastrophic Forgetting in Visual Continual Learning with Reinforcement Fine-Tuning

## 论文信息

- **arXiv ID**: 2605.09640
- **发表日期**: 2026-05-10
- **作者**: Meng Lou, Hanzhong Guo, Linwei Chen et al.
- **方向**: 持续学习 / 强化微调 / 视觉
- **开源**: 待确认

## 摘要（英译中）

近期研究表明，强化微调（RFT）本质上比监督微调（SFT）对灾难性遗忘更具韧性。然而，RFT（如 GRPO）是否能在具有挑战性的视觉持续学习设置（如类增量学习和域增量学习）中有效克服遗忘，仍是一个开放问题。

通过试点研究，作者确认虽然 RFT 一致地优于 SFT，但仍存在不可忽视的遗忘。他们经验性地将这一瓶颈追溯到**轨迹级漂移不可知（Trajectory-level Drift Agnosticism）**：在实现相同任务奖励的候选轨迹中，与前任务策略的 KL 散度差异很大，这与跨顺序任务的灾难性遗忘强相关。

受此洞察启发，作者提出 **Retention-aware Policy Optimization (RaPO)**，由两个核心组件组成：
1. **Retention Reward**：将轨迹级分布漂移转换为连续奖励信号，优先强化每组内保留知识的轨迹
2. **跨任务优势归一化（CTAN）**：在任务边界间保持奖励统计量的持久指数移动平均，以稳定持续学习期间的优化进展

在五个视觉持续学习设置上全面评估 RaPO。大量实验表明，RaPO 达到领先性能，在大幅减少灾难性遗忘的同时保持强可塑性。据作者所知，这项工作代表了在视觉持续学习中首次系统性地探索 RFT。

## 核心贡献

1. **RaPO 方法**：Retention Reward + CTAN 双组件协同
2. **轨迹级漂移不可知**：首次揭示 RFT 遗忘瓶颈的根因
3. **跨任务优势归一化**：稳定跨任务边界的优化
4. **5 个视觉 CL 基准**：涵盖类增量和域增量设置
5. **首个系统性探索**：RFT 在视觉持续学习中的应用

## 关键洞察

> 在实现相同任务奖励的候选轨迹中，与前任务策略的 KL 散度差异很大，这强相关于跨顺序任务的灾难性遗忘。

相同任务奖励不等于相同知识保留程度。RaPO 通过 Retention Reward 将这种分布漂移显式化为可优化的信号。

## 为什么重要

- **RFT 优于 SFT**：为持续学习提供新的微调范式
- **理论洞察**：揭示了"相同奖励≠相同知识保留"的关键问题
- **实用方案**：RaPO 在保持塑性的同时大幅减少遗忘

## 与端侧/移动端的相关性

- 视觉持续学习是移动端和机器人系统的核心需求
- RFT 的在线学习特性适合动态环境
- 减少遗忘意味着更稳定的长期性能

## 参考文献

- 原论文: https://arxiv.org/abs/2605.09640
