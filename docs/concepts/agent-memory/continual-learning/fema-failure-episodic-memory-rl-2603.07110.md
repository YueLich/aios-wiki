---
title: Learning From Failures: Efficient Reinforcement Learning Control with Episodic Memory
arXiv: 2603.07110
date: 2026-03-07
tags: ['agent-memory', 'episodic-memory', 'reinforcement-learning', 'robotics']
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv ID**: 2603.07110
- **发表日期**: 2026-03-07
- **作者**: Chenyang Miao
- **方向**: cs.RO

## 摘要

Reinforcement learning has achieved remarkable success in robot learning. However, under challenging exploration and contact-rich dynamics, early-stage training is frequently dominated by premature terminations such as collisions and falls. As a result, learning is overwhelmed by short-horizon, low-return trajectories, which hinder convergence and limit long-horizon exploration.

To alleviate this issue, we propose a technique called Failure Episodic Memory Alert (FEMA). FEMA explicitly stores short-horizon failure experiences through an episodic memory module. During interactions, it retrieves similar failure experiences and prevents the robot from recurrently relapsing into unstable states, guiding the policy toward long-horizon trajectories with greater long-term value.

FEMA can be combined easily with model-free reinforcement learning algorithms, and yields a substantial sample-efficiency improvement of 33.11% on MuJoCo tasks across several classical RL algorithms. Furthermore, integrating FEMA into a parallelized PPO training pipeline demonstrates its effectiveness on a real-world bipedal robot task.

## 核心贡献

1. **新型记忆系统设计**: 论文提出了结合工作记忆和情景记忆的混合记忆架构，有效解决长时记忆依赖问题
2. **计算效率优化**: 通过固定数量的记忆token实现近常数级的每步计算和内存开销
3. **跨任务泛化**: 记忆系统设计支持跨不同任务场景的泛化能力

## 为什么重要

这篇论文解决了视觉运动策略中非马尔可夫任务的关键挑战——传统方法要么受限于短视上下文，要么通过简单扩大上下文窗口带来巨大计算成本。VPWEM通过模仿人类认知中的记忆压缩机制，用固定数量的情景记忆token表示长历史，在保持计算效率的同时显著提升了在需要长期记忆的机器人操作任务中的表现。

## 与移动端/端侧的相关性

记忆压缩和固定token表示方法对端侧部署具有重要意义——近常数级的内存开销使得该方法适合在资源受限的机器人平台上运行。

## 参考文献

见原论文: https://arxiv.org/abs/2603.07110
