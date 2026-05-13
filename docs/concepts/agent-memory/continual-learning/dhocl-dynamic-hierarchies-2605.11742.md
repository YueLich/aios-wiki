---
title: "Online Continual Learning with Dynamic Label Hierarchies"
arXiv: "2605.11742"
date: "2026-05-12"
tags: [agent-memory, continual-learning, online-continual-learning, dynamic-label-hierarchies, hierarchical-classification]
reviewer: auto
source: arXiv API
---

# Online Continual Learning with Dynamic Label Hierarchies

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Xinrui Wang, Shao-Yuan Li, Bartłomiej Twardowski, Alexandra Gomez-Villa, Songcan Chen |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.11742 |
| **类别** | cs.LG |
| **标签** | agent-memory, continual-learning, online-continual-learning, dynamic-label-hierarchies, hierarchical-classification |

## 摘要（翻译）

在线持续学习（OCL）旨在从无限的非平稳数据流中学习，但现有方法大多假设平坦标签空间，忽略了现实世界概念的水平演化（兄弟类别）和垂直演化（粗粒度或细粒度类别）的层次组织。本文提出新问题设置 DHOCL（动态层次在线持续学习），其中分类法跨粒度演化，每个样本在单一层次级别提供监督。发现两个根本性问题：（i）混合粒度下的部分监督仅提供沿演化路径的逐点信号，限制了可塑性并破坏了跨层次语义一致性；（ii）现有方法缺乏捕获层级结构的归纳偏置。

## 核心贡献

1. **DHOCL 问题设置**：首个考虑动态层级演化的在线持续学习问题框架，更接近真实世界知识结构的演化模式
2. **路径感知监督机制**：提出沿层级路径提供监督信号的方法，解决部分监督的局限性
3. **层级结构归纳偏置**：设计专门捕获层级结构的模型组件，提升跨层次语义一致性
4. **实验验证**：在新设计的 DHOCL 基准上验证方法的有效性

## 为什么重要

DHOCL 揭示了持续学习的一个被忽视的维度：**知识的层级结构本身是动态演化的**。对于 Agent 记忆系统，这意味着记忆的层级组织不应是静态的，而应能够适应新概念的加入并重组层级结构。这对构建能够终身学习的 Agent 记忆系统具有重要启示。

## 与移动端/端侧的相关性

- 在线学习特性适合端侧持续学习场景，无需存储完整数据集
- 层级结构的显式建模可降低记忆检索的复杂度，提升端侧检索效率
- 路径感知监督机制可减少端侧学习所需的标注数据量

## 参考文献

- Wang, X., Li, S.-Y., Twardowski, B., Gomez-Villa, A., & Chen, S. (2026). Online Continual Learning with Dynamic Label Hierarchies. arXiv:2605.11742.
