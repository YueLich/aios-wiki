---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-30
authors: ["Kathrin Korte", "Joachim Winter Pedersen", "Eleni Nisioti"]
tags: [agent-memory, continual-learning, modularity, representation-geometry, dimensionality]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.27656
- **作者**: Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti
- **提交日期**: 2026-04-30
- **方向**: 持续学习 / 模块化 / 表示几何

## 摘要（全文翻译）

为保留已学表示，持续学习系统必须在可塑性（获取新知识的能力）和稳定性（保留已学知识的能力）之间取得平衡。这种稳定-可塑性困境影响表示如何在任务间复用：共享结构在任务相似时支持迁移，但在新学习干扰已有表示时也会产生干扰。

本文研究**维度在控制模块化如何塑造表示几何**中的作用。

## 核心贡献

1. **维度作为关键控制变量**：维度决定了模块化结构何时有助于 CL
2. **稳定-可塑性的表示几何分析**：从几何角度分析模块化对 CL 的影响
3. **共享 vs 干扰的边界条件**：明确了模块化在什么条件下促进迁移而非干扰

## 为什么重要

这篇论文从几何角度深化了对 CL 中模块化作用的理解：模块化不是总是有益的，其效果高度依赖于表示空间的维度。在高维空间模块化可能导致过度碎片化，在低维空间则可能有效隔离不同任务。
