---
title: "Forager: A Lightweight Testbed for Continual Learning with Partial Observability in RL"
arXiv: 2605.01131
date: 2026-05-01
tags: [agent-memory, continual-learning, reinforcement-learning, partial-observability]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **作者**: Steven Tang, Xinze Xiong, Anna Hakhverdyan, Andrew Patterson, Jacob Adkins
- **发表**: 2026-05-01
- **方向**: 持续学习 · 强化学习 · 部分可观测性

## 摘要（翻译）

在持续强化学习（CRL）中，好的性能需要永不停歇的学习、行动和探索——在一个大型、部分可观测的世界中。大多数 CRL 实验集中在**塑性丧失（loss of plasticity）**——在一次性实验中添加一些非平稳性到经典完全可观测 MDP 中。此外，这些实验很少考虑**部分可观测性的作用**以及**使用记忆或递归的 CRL Agent 的重要性**。

部分可观测 CRL 环境成本高昂是一个可能的原因。本文引入 **Forager**，一个轻量级部分可观测 CRL 环境，具有恒定内存占用。我们提供了一组实验和示例任务，证明 Forager 对当前 CRL Agent 具有挑战性，同时支持深入研究。实验表明：
- Agent 表现出塑性丧失
- 提议的缓解措施有所帮助
- **最有用的是利用状态构建（state construction）**

本文还介绍了一种生成无尽新任务流的 Forager 变体，显著突出了当前 CRL Agent 的局限性。

## 为什么重要

Forager 填补了 CRL 评估中的一个关键空白：
1. **部分可观测性**：真实世界 Agent（机器人、VR/AR 助手）面对的正是部分可观测环境
2. **轻量级**：之前的部分可观测 CRL 环境成本过高，限制了研究规模
3. **恒定内存占用**：便于在资源受限环境（如移动端）部署研究

## 关键发现

- 当前 CRL 方法在有记忆需求的部分可观测场景下表现不佳
- 状态构建（利用记忆构建对环境的内部表示）是最有效的策略
- 塑性丧失在有记忆的 Agent 中仍然存在

## 与移动端/端侧的相关性

移动端 Reinforcement Learning Agent 天然面临部分可观测性：
- 手机传感器只能感知环境的部分状态
- 用户的长期偏好需要记忆系统维护
- Forager 的轻量级设计（恒定内存占用）对移动端 RL 研究有直接参考价值

---

*注：本文为新发现论文（2605.01131）。*
