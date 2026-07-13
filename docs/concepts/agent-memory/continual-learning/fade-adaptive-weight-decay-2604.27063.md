---
title: "Learning to Forget: Continual Learning with Adaptive Weight Decay"
arXiv: 2604.27063
date: 2026-04-29
tags: [continual-learning, memory-compression, theory]
reviewer: auto
source: arXiv RSS/API
---

# Learning to Forget: Continual Learning with Adaptive Weight Decay

## 论文基本信息

- **arXiv ID**: 2604.27063
- **作者**: Aditya A. Ramesh, Alex Lewandowski, Jürgen Schmidhuber
- **提交日期**: 2026-04-29
- **类别**: cs.LG, cs.NE

## 摘要

具有有限容量的持续学习 Agent 必须在获取新知识与保留旧知识之间取得平衡。这要求对不再需要的知识进行受控遗忘以释放学习容量。权重衰减作为一种遗忘机制，可以通过逐渐丢弃存储在权重中的信息来实现这一点。然而，固定标量权重衰减在时间和所有参数上均匀地驱动遗忘，即使某些参数编码稳定知识而其他参数跟踪快速变化目标时亦然。本文提出 FADE（Forgetting through Adaptive Decay），通过近似梯度下降在线调整每个参数的自适应权重衰减率。论文为在线线性设置推导出 FADE 并应用于神经网络最后一层，发现 FADE 自动发现不同参数的不同衰减率、一致性改进固定权重衰减。

## 核心贡献

1. **自适应参数级权重衰减**：FADE 为每个参数学习独立的衰减率，而非全局标量。
2. **理论保证**：为在线线性设置提供 FADE 的收敛性证明。
3. **实践验证**：在多种持续学习任务上验证 FADE 超越固定权重衰减。
4. **与 Schmidhuber 合作**：NeurIPS 社区持续学习元老的最新工作。

## 为什么重要

FADE 将「何时遗忘」从手工设计规则转变为自适应学习问题。传统方法需要人工设定哪些知识该保留、哪些该丢弃，FADE 通过元学习自动发现这一点。更重要的是，这是少数从参数权重层面处理遗忘的方法，而非依赖外部记忆系统。对端侧持续学习的启示：端侧模型无法依赖外部存储时，参数层面的自适应遗忘尤为重要。

## 与移动端/端侧相关性

- 端侧模型（手机 SoC、NPU）存储和计算受限，参数级自适应遗忘比外部记忆更高效
- FADE 的 per-parameter 衰减率适合稀疏推理硬件（可以只激活相关参数路径）
- 持续学习对移动端多场景适应（室内/户外/驾驶等）有直接应用
