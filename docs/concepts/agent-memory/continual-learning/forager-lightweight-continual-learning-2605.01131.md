---
title: "Forager: A Lightweight Testbed for Continual Learning with Partial Observability in RL"
arXiv: 2605.01131
date: 2026-05-01
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Forager: A Lightweight Testbed for Continual Learning with Partial Observability in RL

**作者:** Steven Tang, Xinze Xiong, Anna Hakhverdyan, Andrew Patterson, Jacob Adkins, Jiamin He, Esraa Elelimy, Parham Mohammad Panahi, Martha White, Adam White
**发表:** 2026-05-01

## 摘要

In continual reinforcement learning (CRL), good performance requires never-ending learning, acting, and exploration in a big, partially observable world. Most CRL experiments have focused on loss of plasticity -- the inability to keep learning -- in one-off experiments where some unobservable non-stationarity is added to classic fully observable MDPs. Further, these experiments rarely consider the role of partial observability and the importance of CRL agents that use memory or recurrence. One potential reason for this focus on mitigating loss of plasticity without considering partial observability is that many partially-observable CRL environments are prohibitively expensive. In this paper, we introduce Forager, a light-weight partially-observable CRL environment with a constant memory footprint.

## 核心贡献

1. **Forager 环境**: 轻量级部分可观测持续强化学习环境，内存占用恒定，适合大规模 CRL 实验
2. **部分可观测性系统研究**: 首次在 CRL 背景下系统研究部分可观测性和记忆/循环机制的重要性
3. **Loss of Plasticity vs. 部分可观测**: 证明当前 CRL 智能体在 Forager 上表现出可塑性丧失，但利用状态构建是最有效的缓解方法
4. **无限任务流变体**: 提供持续生成新任务的变体，清晰揭示当前 CRL 智能体的局限性

## 为什么重要

现有 CRL 研究大多在完全可观测 MDP 上测试，忽视了真实世界中的部分可观测性。Forager 填补了这一空白，使研究者能够在轻量环境中系统研究记忆和循环对 CRL 的重要性。这对设计能够在真实环境中持续学习的 Agent 系统（尤其是需要记忆的端侧 Agent）有重要启发。

## 与端侧/移动端的相关性

端侧 Agent 面临的核心挑战正是部分可观测性——移动设备上的感知输入（摄像头、麦克风、传感器）都是不完整的世界观测。Forager 的发现表明，利用状态构建（state construction）是缓解端侧 CRL 可塑性丧失的最有效方法。
