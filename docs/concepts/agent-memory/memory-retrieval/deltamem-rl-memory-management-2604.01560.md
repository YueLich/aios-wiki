---
title: "DeltaMem: Towards Agentic Memory Management via Reinforcement Learning"
arXiv: 2604.01560
date: 2026-04-02
authors: ["Qi Zhang et al."]
tags: [agent-memory, memory-retrieval, RL, memory-management, persona-memory]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.01560
- **作者**: Qi Zhang, Shen Huang, Chu Liu et al.
- **提交日期**: 2026-04-02
- **方向**: 强化学习记忆管理 / Agent 记忆 / 人格记忆

## 摘要（全文翻译）

以人格为中心的记忆的近期进展揭示了多 Agent 系统在管理人格记忆方面的强大能力，尤其是在会话场景中。然而，这些复杂框架容易遭受信息丢失，在不同场景中脆弱，导致性能次优。

本文提出 **DeltaMem**，一个 Agent 记忆管理系统，将以人格为中心的记忆管理表述为端到端任务。灵感来自人类记忆的演化，合成用户-助手对话数据集，并配以相应的操作级记忆更新标签。在此基础上，引入了基于记忆的 Levenshtein 距离来衡量记忆更新质量。

## 核心贡献

1. **RL 驱动的人格记忆管理**：将记忆更新决策建模为强化学习问题
2. **人类记忆演化启发**：借鉴人类记忆如何随时间演化的机制
3. **记忆 Levenshtein 距离**：衡量记忆更新质量的新指标
4. **端到端优化**：而非手工记忆更新规则

## 为什么重要

DeltaMem 用 RL 替代手工的记忆更新规则，这是记忆管理自动化的重要一步。核心洞察：记忆更新不是简单的"写入"，而是需要智能地决定"如何修改现有记忆"——这正是 RL 的强项。
