---
title: "Sinkhorn Based Associative Memory Retrieval Using Spherical Hellinger Kantorovich Dynamics"
arXiv: 2603.20656
date: 2026-03-21
authors: ["Aratrika Mustafi", "Soumya Mukherjee"]
tags: [agent-memory, associative-memory, optimal-transport, mathematical-foundations, memory-representation]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2603.20656
- **发表日期**: 2026-03-21
- **作者**: Aratrika Mustafi, Soumya Mukherjee
- **方向**: 记忆表示理论基础（最优传输的联想记忆）

## 摘要

**背景**：传统 Hopfield 网络的联想记忆容量受限于存储模式数量，需要容量理论指导设计。

**方法**：为经验测度（加权点云）提出密集联想记忆。存储模式和查询都是有限支撑概率测度，检索定义为最小化基于去偏 Sinkhorn 散度的 Hopfield 风格对数-和-指数能量。将检索动力学推导为球面 Hellinger Kantorovich（SHK）梯度流，同时更新支撑位置和权重。离散化后得到确定性算法，使用 Sinkhorn 势计算重心传输步骤和乘法单纯形重加权。

**理论结果**：在局部分离和 PL-type 条件下，证明盆地不变性、几何收敛到局部最小化，以及最小化子保持接近相应存储模式。在随机模式模型下，进一步证明这些 Sinkhorn 盆地高概率不相交，蕴含指数级容量。

**实验**：在合成高斯点云记忆上验证了从扰动查询中的鲁棒恢复能力。

## 核心贡献

1. **最优传输联想记忆**：首次将 Sinkhorn 散度和球面 Hellinger Kantorovich 梯度流引入联想记忆理论
2. **指数容量保证**：在随机模式模型下证明不相交 basins，高概率指数容量
3. **权重学习**：同时学习支撑位置和权重，而非仅学习权重
4. **确定性算法**：离散化后无需随机搜索，算法可解释性强

## 为什么重要

联想记忆是 Agent 记忆系统的理论基础：

- **容量问题**：Hopfield 网络的容量问题困扰学界多年，本文通过最优传输框架提供了新的理论视角
- **几何收敛保证**：本文提供的是确定性收敛保证，而非概率近似
- **点云表示**：经验测度（点云）比传统二元模式更通用，可应用于视觉和感知数据

## 与端侧/移动端的相关性

对端侧记忆系统有理论指导意义：

- **高效检索**：Sinkhorn 算法已有高效 GPU 实现，适合边缘加速
- **概率记忆表示**：点云/测度表示比向量更灵活，适合传感器数据
- **确定性算法**：无需随机初始化，边缘部署更稳定

## 参考文献

- arXiv: 2603.20656 | https://arxiv.org/abs/2603.20656
