---
title: "DeltaMem: Towards Agentic Memory Management via Reinforcement Learning"
arXiv: 2604.01560
date: 2026-04-02
tags: [agent-memory, memory-retrieval, reinforcement-learning]
reviewer: auto
source: arXiv RSS/API
---

# DeltaMem: Towards Agentic Memory Management via Reinforcement Learning

## 论文基本信息

- **作者**: Qi Zhang, Shen Huang, Chu Liu, Shouqing Yang, Junbo Zhao, Haobo Wang, Pengjun Xie
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2604.01560
- **代码**: （待补充）

## 核心贡献

1. **DeltaMem 系统**: 提出 DeltaMem，一个 Agentic 记忆管理系统，在单一智能体设置中将人格中心记忆管理表述为端到端任务。
2. **人类记忆启发**: 灵感来自人类记忆的进化，合成用户-助手对话数据集及相应的操作级记忆更新标签。
3. **Memory-based Levenshtein Distance**: 引入基于记忆的 Levenshtein 距离来形式化记忆更新奖励。
4. **定制强化学习框架**: 提出定制的强化学习框架以进一步增强 DeltaMem 的管理能力。
5. **最优基线**: 在 LoCoMo、HaluMem 和 PersonaMem 等多个长期记忆基准上，训练自由和 RL 训练的 DeltaMem 均优于所有产品级基线。

## 研究背景与问题

以人格为中心的记忆的最新进展揭示了多智能体系统在管理人格记忆方面的强大能力，尤其是在对话场景中。然而，这些复杂框架存在信息丢失问题，且在不同场景下脆弱，导致性能次优。

## 核心方法

### 端到端记忆管理
将人格中心记忆管理表述为端到端任务，在单一智能体设置内完成。

### Memory-based Levenshtein Distance
受人类记忆进化启发，引入基于记忆的 Levenshtein 距离：
- 衡量记忆更新前后的差异
- 形式化记忆更新奖励信号

### 强化学习增强
基于定制 RL 框架进一步增强记忆管理能力。

## 实验结果

在多个长期记忆基准（LoCoMo、HaluMem、PersonaMem）上，**训练自由和 RL 训练的 DeltaMem 均优于所有产品级基线**。

## 为什么重要

DeltaMem 将强化学习应用于记忆管理，为 Agentic 记忆系统开辟了新的优化方向。Memory-based Levenshtein Distance 的设计——用编辑距离衡量记忆更新的质量——是一个创新性的奖励塑形方法。

## 与移动端/端侧相关性

端侧个性化 Agent 需要高效管理用户人格记忆。DeltaMem 在 LoCoMo 等真实世界基准上超越产品级系统，证明了 RL 优化记忆管理的潜力，对端侧记忆管理系统的设计有直接参考价值。
