---
title: "DeltaMem: Towards Agentic Memory Management via Reinforcement Learning"
arXiv: 2604.01560
date: 2026-04-02
tags: [agent-memory, memory-management, reinforcement-learning, persona-memory]
reviewer: auto
source: arXiv API
authors: "Qi Zhang, Shen Huang, Chu Liu"
---

## 论文信息

- **arXiv**: 2604.01560
- **发表日期**: 2026-04-02
- **作者**: Qi Zhang, Shen Huang, Chu Liu
- **方向**: 记忆管理与强化学习

## 摘要

近年来，以角色为中心的记忆进展揭示了多 Agent 系统在管理角色记忆方面的强大能力，特别是在对话场景中。然而，这些复杂框架往往存在信息损失且在不同场景中脆弱，导致性能欠佳。本文提出 DeltaMem，一种 Agent 记忆管理系统，将在单 Agent 设置中将角色中心记忆管理表述为端到端任务。为进一步提升 DeltaMem 的记忆管理能力，本文从人类记忆演化中获得灵感，综合用户-助手对话数据集及相应的操作级记忆更新标签。在此基础上，本文引入了一种新型的基于记忆的 Levenshtein 距离来形式化记忆更新奖励，并提出了定制强化学习框架来增强 DeltaMem 的管理能力。大量实验表明，无论是否经过 RL 训练，DeltaMem 在各长期记忆基准上均优于所有产品级基线，包括 LoCoMo、HaluMem 和 PersonaMem。

## 核心贡献

1. **RL 驱动记忆管理**：将记忆管理决策（何时更新、如何合并冲突）建模为 RL 问题
2. **记忆 Levenshtein 距离**：设计新型奖励函数衡量记忆更新的质量
3. **单 Agent 框架**：简化多 Agent 协调复杂度，聚焦记忆管理本身
4. **全面超越产品级基线**：在 LoCoMo、HaluMem、PersonaMem 三大基准上均达最优

## 为什么重要

记忆管理涉及复杂的决策：哪些信息值得写入、如何合并来自不同会话的冲突更新、如何遗忘过时内容。DeltaMem 将这些问题形式化为 RL 问题并通过学习找到最优策略，相比人工设计的规则更加自适应。对端侧 Agent，这意味着记忆系统可以学会适应个人用户的偏好和使用模式。

### 与移动端/端侧的相关性

- **个性化适应**：RL 框架可学习特定用户的记忆偏好
- **自动化管理**：无需人工设计规则，降低维护成本
- **跨基准泛化**：在多个基准上验证的通用性
