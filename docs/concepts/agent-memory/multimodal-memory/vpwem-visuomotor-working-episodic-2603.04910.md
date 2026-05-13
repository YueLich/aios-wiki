---
title: VPWEM: Non-Markovian Visuomotor Policy with Working and Episodic Memory
arXiv: 2603.04910
date: 2026-03-05
tags: ['agent-memory', 'multimodal-memory', 'episodic-memory', 'robotics', 'vision']
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv ID**: 2603.04910
- **发表日期**: 2026-03-05
- **作者**: Yuheng Lei, Zhixuan Liang, Hongyuan Zhang
- **方向**: cs.RO

## 摘要

Imitation learning from human demonstrations has achieved significant success in robotic control, yet most visuomotor policies still condition on single-step observations or short-context histories, making them struggle with non-Markovian tasks that require long-term memory.

Simply enlarging the context window incurs substantial computational and memory costs and encourages overfitting to spurious correlations, leading to catastrophic failures under distribution shift and violating real-time constraints in robotic systems. By contrast, humans can compress important past experiences into long-term memories and exploit them to solve tasks throughout their lifetime.

In this paper, we propose VPWEM, a non-Markovian visuomotor policy equipped with working and episodic memories. VPWEM retains a sliding window of recent observation tokens as short-term working memory, and introduces a Transformer-based contextual memory compressor that recursively converts out-of-window observations into a fixed number of episodic memory tokens. The compressor uses self-attention over a cache of past summary tokens and cross-attention over a cache of historical observations, and is trained jointly with the policy.

We instantiate VPWEM on diffusion policies to exploit both short-term and episode-wide information for action generation with nearly constant memory and computation per step. Experiments demonstrate that VPWEM outperforms state-of-the-art baselines including diffusion policies and vision-language-action (VLA) models by more than 20% on the memory-intensive manipulation tasks in MIKASA and achieves an average 5% improvement on the mobile manipulation benchmark MoMaRT.

## 核心贡献

1. **新型记忆系统设计**: 论文提出了结合工作记忆和情景记忆的混合记忆架构，有效解决长时记忆依赖问题
2. **计算效率优化**: 通过固定数量的记忆token实现近常数级的每步计算和内存开销
3. **跨任务泛化**: 记忆系统设计支持跨不同任务场景的泛化能力

## 为什么重要

这篇论文解决了视觉运动策略中非马尔可夫任务的关键挑战——传统方法要么受限于短视上下文，要么通过简单扩大上下文窗口带来巨大计算成本。VPWEM通过模仿人类认知中的记忆压缩机制，用固定数量的情景记忆token表示长历史，在保持计算效率的同时显著提升了在需要长期记忆的机器人操作任务中的表现。

## 与移动端/端侧的相关性

记忆压缩和固定token表示方法对端侧部署具有重要意义——近常数级的内存开销使得该方法适合在资源受限的机器人平台上运行。

## 参考文献

见原论文: https://arxiv.org/abs/2603.04910
