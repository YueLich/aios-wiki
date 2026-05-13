---
title: "Beyond Point-wise Neural Collapse: A Topology-Aware Hierarchical Classifier for Class-Incremental Learning"
arXiv: "2605.11904"
date: "2026-05-12"
tags: [agent-memory, continual-learning, class-incremental-learning, neural-collapse, topology-aware]
reviewer: auto
source: arXiv API
---

# Beyond Point-wise Neural Collapse: A Topology-Aware Hierarchical Classifier for Class-Incremental Learning

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Huiyu Yi, Zhiming Xu, Dunwei Tu, Zhicheng Wang, Baile Xu, Furao Shen |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.11904 |
| **类别** | cs.CV |
| **标签** | agent-memory, continual-learning, class-incremental-learning, neural-collapse, topology-aware |

## 摘要（翻译）

最近类均值（NCM）分类器因其相比全连接层更强的抗灾难性遗忘能力，在类别增量学习（CIL）中受到青睐。神经崩溃（NC）理论通过假设特征塌缩为单点来支持 NCM 的最优性，但非线性特征漂移和 CIL 中训练不足通常阻止这种理想状态。因此，类别表现为复杂流形而非塌缩点，导致单点 NCM 次优。本文提出 HC-SOINN，通过"局部到全局"的表示捕获流形的拓扑结构。同时提出 STAR 方法，利用残差进行结构-拓扑对齐，使分类器能够适应复杂的类内变化。

## 核心贡献

1. **HC-SOINN 分类器**：首个在 CIL 中利用流形拓扑结构的方法，通过分层聚类捕获类别的局部到全局拓扑
2. **STAR 结构-拓扑对齐**：通过残差学习实现特征空间与拓扑空间的对齐，提高分类器的判别能力
3. **理论基础**：将 NC 理论从单点假设扩展到流形假设，更准确地描述实际学习过程中的特征分布
4. **实验验证**：在多个 CIL 基准上验证了拓扑感知方法相比单点 NCM 的优越性

## 为什么重要

这篇论文揭示了类别增量学习中特征分布的真实结构——不是 NC 理论假设的完美塌缩点，而是复杂的流形结构。这对 Agent 记忆系统的启示是：**Agent 的记忆表示不应被约束为简单的原型向量，而应保留记忆项之间的拓扑关系**。记忆流形的完整性对于 Agent 在新任务中的零样本泛化至关重要。

## 与移动端/端侧的相关性

- 拓扑感知分类器相比深度学习方法通常参数量更少，适合端侧部署
- HC-SOINN 的在线聚类特性无需存储所有历史样本，符合端侧记忆压缩需求
- 结构-拓扑对齐方法可用于在端侧构建轻量级的记忆层次结构

## 参考文献

- Yi, H., Xu, Z., Tu, D., Wang, Z., Xu, B., & Shen, F. (2026). Beyond Point-wise Neural Collapse: A Topology-Aware Hierarchical Classifier for Class-Incremental Learning. arXiv:2605.11904.
