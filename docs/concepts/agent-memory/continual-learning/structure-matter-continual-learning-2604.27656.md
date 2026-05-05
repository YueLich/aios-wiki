---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-30
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry

## 论文基本信息

- **作者**: Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti, Sebastian Risi
- **arXiv**: https://arxiv.org/abs/2604.27656
- **领域**: cs.LG


## 摘要

To preserve previously learned representations, continual learning systems must strike a balance between plasticity, the ability to acquire new knowledge, and stability. This stability-plasticity dilemma affects how representations can be reused across tasks: shared structure enables transfer when tasks are similar but may also induce interference when new learning disrupts existing representations. However, it remains unclear when and why structural separation influences this trade-off. In this study, we examine how network architecture, task similarity, and representational dimensionality jointly shape learning in a sequential task paradigm inspired by transfer-interference studies. We compare a task-partitioned modular recurrent network with a single-module baseline by systematically varying task similarity (low, medium, high) and the scale of weight initialization, which induces different learning regimes that we empirically characterize through the effective dimensionality of the learned representations. We find that architecture has minimal impact in high-dimensional regimes where representations are sufficiently unconstrained to accommodate multiple tasks without strong interference. In contrast, in lower-dimensional (rich) regimes, architectural separation is decisive: modular networks exhibit graded alignment of task-specific subspaces with overlap for similar tasks, partial orthogonalization for moderately dissimilar tasks, and stronger separation for dissimilar tasks. This graded geometry is absent in the single network baseline. Our findings suggest that representational dimensionality acts as a key organizing variable governing when structural separation becomes functionally relevant, and highlight adaptive geometry as a central principle for designing continual learning systems.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
