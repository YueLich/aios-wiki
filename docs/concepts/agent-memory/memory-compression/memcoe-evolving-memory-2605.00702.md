---
title: "MemCoE: Learning How and What to Memorize — Cognition-Inspired Two-Stage Optimization for Evolving Memory"
arXiv: 2605.00702
date: 2026-05-01
tags: [agent-memory, memory-compression, continual-learning, RL]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **作者**: Derong Xu, Shuochen Liu, Pengfei Luo, Pengyue Jia, Yingzi Zhang
- **发表**: 2026-05-01
- **方向**: 记忆压缩 · 持续学习 · 强化学习

## 摘要（翻译）

LLM Agent 需要长期用户记忆以实现一致的个性化，但有限的上下文窗口阻碍了长时间交互中演化偏好的追踪。现有的记忆系统主要依赖**静态、手工设计的更新规则**；虽然基于强化学习（RL）的 Agent 学习记忆更新，但**稀疏的结果奖励提供弱监督**，导致不稳定的长期优化。

本文从记忆 schema 理论和前额叶区域与海马区域的功能分工中获得启发，提出 **MemCoE**，一个认知启发的两阶段优化框架，学习记忆应该如何组织以及应该更新什么信息：

- **第一阶段（Memory Guideline Induction）**：通过对比反馈优化全局 guideline，将其解释为文本梯度
- **第二阶段（Guideline-Aligned Memory Policy Optimization）**：用诱导的 guideline 定义结构化过程奖励，执行多轮 RL 学习 guideline-following 记忆演化策略

在三个涵盖显式/隐式偏好、不同规模和噪声的个性化记忆基准上，MemCoE 持续超越强基线，并表现出良好的鲁棒性、可迁移性和效率。

## 核心贡献

1. **两阶段认知启发框架**：将"记忆如何组织"和"记忆更新什么"解耦为两个独立的优化问题
2. **Memory Guideline Induction**：通过对比反馈从数据中学习记忆组织的全局 principle
3. **过程奖励的 RL 而非稀疏结果奖励**：解决了记忆演化任务中奖励稀疏的问题
4. **跨 benchmark 持续改进**：在有噪声和不同偏好设置下均有效

## 为什么重要

记忆压缩和记忆更新的核心问题不仅是"存储什么"，还包括"如何判断新信息是否值得更新现有记忆"。MemCoE 的两阶段框架：
- 第一阶段学习"记忆组织的抽象原则"
- 第二阶段学习"遵循这些原则的具体更新行为"

这种分离使系统能够在新场景中更好地泛化，避免了端到端 RL 在稀疏奖励下的不稳定性。

## 与移动端/端侧的相关性

移动端个性化记忆系统的核心挑战：
- 用户偏好随时间演化，需要动态记忆更新
- 移动端无法承载大规模上下文窗口
- MemCoE 的高效 RL 方法和记忆压缩思路对端侧部署有直接价值

---

*注：本文为新发现论文（2605.00702）。*
