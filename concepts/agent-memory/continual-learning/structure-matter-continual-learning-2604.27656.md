---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-30
tags: [continual-learning, memory-retrieval, modularity, representational-geometry]
reviewer: auto
source: arXiv RSS/API
---

# When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry

## 论文基本信息

- **arXiv ID**: 2604.27656
- **作者**: (From paper)
- **提交日期**: 2026-04-30
- **类别**: cs.LG, cs.AI

## 摘要

To preserve previously learned representations, continual learning systems must strike a balance between plasticity (the ability to acquire new knowledge) and stability. This stability-plasticity dilemma affects how representations can be reused across tasks: shared structure enables transfer when tasks are similar but may also induce interference when new learning disrupts existing representations. However, it remains unclear when and why structural separation influences this trade-off. In this study, we examine how network architecture, task similarity, and representational dimensionality jointly shape learning in a sequential task paradigm. We compare a task-partitioned modular recurrent network with a single-module baseline by systematically varying task similarity (low, medium, high) and the scale of weight initialization, which induces different learning regimes. We find that architecture has minimal impact in high-dimensional regimes where representations are sufficiently unconstrained. In contrast, in lower-dimensional (rich) regimes, architectural separation is decisive: modular networks exhibit graded alignment of task-specific subspaces with overlap for similar tasks, partial orthogonalization for moderately dissimilar tasks, and stronger separation for dissimilar tasks.

## 核心贡献

1. **维度作为组织变量**：揭示表征维度是决定结构分离何时起作用的关键组织变量。
2. **高维 vs 低维 regimes**：高维 regime 下架构影响最小；低维（rich）regime 下模块化架构决定性更强。
3. **分级几何对齐**：模块化网络在相似任务上部分重叠，在中等不相似任务上部分正交化，在高度不相似任务上强分离。
4. **对 CL 设计的启示**：维度丰富的环境下，结构分离对持续学习至关重要；对维度受限的移动端更有价值。

## 为什么重要

这篇论文回答了持续学习中一个基本问题：模块化架构何时重要？发现在高维「未充分约束」的表征空间中，任务可以共存而不会强烈干扰——因此模块化结构影响不大。但在低维「丰富」空间中，结构分离是决定性的。这对移动端持续学习系统设计有直接意义：端侧设备的计算资源受限，表征维度可能天然受限，模块化架构的价值更大。

## 与移动端/端侧相关性

- 移动端是天然的「低维丰富」环境——计算和存储资源限制迫使表征维度受限
- 移动端持续学习场景：用户持续使用 App，不同任务有不同但重叠的特征空间
- 移动端模型（MobileLLM、Phi-4 等）表征维度相对有限，模块化设计的价值可能更大
- 对理解移动端持续学习系统的稳定性-可塑性权衡有理论指导意义
