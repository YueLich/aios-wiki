---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-30
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry

**作者:** Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti, Sebastian Risi  
**发表:** 2026-04-30

## 摘要

To preserve previously learned representations, continual learning systems must strike a balance between plasticity, the ability to acquire new knowledge, and stability. This stability-plasticity dilemma affects how representations can be reused across tasks: shared structure enables transfer when tasks are similar but may also induce interference when new learning disrupts existing representations. However, it remains unclear when and why structural separation influences this trade-off. In this study, we examine how network architecture, task similarity, and representational dimensionality jointly shape learning in a sequential task paradigm inspired by transfer-interference studies. We compare a task-partitioned modular recurrent network with a single-module baseline by systematically varying task similarity (low, medium, high) and the scale of weight initialization, which induces different learning regimes that we empirically characterize through the effective dimensionality of the learned representations. We find that architecture has minimal impact in high-dimensional regimes where representations are sufficiently unconstrained to accommodate multiple tasks without strong interference. In contrast, in lower-dimensional (rich) regimes, architectural separation is decisive: modular networks exhibit graded alignment of task-specific subspaces with overlap for similar tasks, partial orthogonalization for moderately dissimilar tasks, and stronger separation for dissimilar tasks. This graded geometry is absent in the single network baseline. Our findings suggest that representational dimensionality acts as a key organizing variable governing when structural separation becomes functionally relevant, and highlight adaptive geometry as a central principle for designing continual learning systems.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
