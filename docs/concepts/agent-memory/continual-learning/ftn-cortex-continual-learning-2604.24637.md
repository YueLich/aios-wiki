---
title: Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks
arXiv: 2604.24637
date: 2026-04-27
tags: [agent-memory, continual_learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.24637
- **作者**: Kevin McKee, Thomas Hazy, Yicong Zheng, Zacharie Bugaud, Thomas Miconi
- **提交日期**: 2026-04-27

## 摘要

Block-sequential continual learning demands that a single model both protect prior solutions from catastrophic forgetting and efficiently infer at inference time which prior solution matches the current input without task labels.

We present Functional Task Networks (FTN), a parameter-isolation method inspired by structural and dynamical motifs found in the mammalian neocortex. Similar to mixture-of-experts, this method uses a high-dimensional, self-organizing binary mask over a large population of small but deep networks, inspired by dendritic models of pyramidal neurons.

The mask is produced by a sparse coding mechanism that learns to decompose the input space into non-overlapping representational slots, each associated with a dedicated sub-network. Importantly, slot assignment is fully unsupervised at both training and inference time: the system self-organizes without requiring task identity labels during either training or deployment.

When a new task arrives, previously unused slots are instantiated for the new patterns while existing slots remain protected. At inference, the sparse mask naturally routes inputs to appropriate task-specific modules. This approach directly addresses the "which prior solution?" inference problem without relying on oracle task labels.

Experiments on multiple continual learning benchmarks demonstrate that FTN achieves state-of-the-art performance while requiring no task identity at inference, moving toward truly unsupervised continual learning in the mammalian cortex.

## 核心贡献

1. **问题定义**: Cortex-Inspired Continual Learning 针对 continual learning 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 continual、learning 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
