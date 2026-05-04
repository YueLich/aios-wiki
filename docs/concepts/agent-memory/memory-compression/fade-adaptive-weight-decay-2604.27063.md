---
title: "Learning to Forget: Continual Learning with Adaptive Weight Decay"
arXiv: 2604.27063
date: 2026-04-29
authors: "Aditya A. Ramesh, Alex Lewandowski, Jürgen Schmidhuber (IDSIA, University of Alberta, KAUST)"
tags: [agent-memory, continual-learning, selective-forgetting, adaptive-weight-decay, theory]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2604.27063v1
- **发表**: 2026-04-29
- **作者**: Aditya A. Ramesh, Alex Lewandowski, Jürgen Schmidhuber (IDSIA, KAUST)
- **方向**: 持续学习 / 遗忘机制
- **开源**: 待确认

---

## 核心思想

**FADE = Forgetting through Adaptive Decay**

将"学习何时遗忘"形式化为**自适应权重衰减**问题。在持续学习场景中，自适应遗忘比固定策略更有效——网络通过学习主动调整哪些权重应该被抑制。

---

## 方法论

### FADE for Online Linear Regression

从最简单的设置开始：在线线性回归中的遗忘控制。

### FADE with Neural Networks

扩展到非线性网络。关键是推导出**每层的自适应衰减速率** γ_i，而非使用全局衰减率。

### 与IDBD的结合

IDBD (Individuated Controller for Beta and gamma)：
- 独立控制每个学习率参数 (β)
- 独立控制每个衰减参数 (γ)

### FADE + Adam

支持Adam优化器——保留Adam的自适应学习率机制，同时叠加FADE的遗忘控制。

---

## 关键数学形式

### γ_i 更新推导

权重衰减项的衰减速率 γ_i 通过**元学习**方式自动调整：
- 每个权重有自己的遗忘速率
- 遗忘速率根据其对当前任务的贡献自适应变化

### 稳定性-可塑性分析

FADE通过选择性遗忘解决了标准权重衰减的两个局限：
1. 固定衰减率无法区分重要和不重要的权重
2. 全局衰减会伤害有用的知识

---

## 实验验证

### 1. 线性跟踪设置

| 设置 | σ_n = 0 | σ_n = 1 |
|---|---|---|
| SGD | 基线 | 基线 |
| SGD + WD | 轻微改善 | 改善 |
| IDBD | 改善 | 改善 |
| IDBD + WD | 更好 | 更好 |
| **FADE** | **最好** | **最好** |

### 2. 非线性跟踪

FADE + Adam 在所有配置中一致地超越基线。

### 3. 流式图像分类（标签排列）

FADE在所有层都有效，并支持部分标签排列的增量学习。

---

## 为什么重要

Schmidhuber 团队将**生物启发的遗忘机制**形式化为可学习的自适应权重衰减系统。这是继"Learning to Forget"(2016)之后，IDSIA在遗忘机制上的又一次重要推进。

### 与移动端/端侧的相关性

- **端侧持续学习**：FADE的增量特性适合设备上运行
- **资源受限场景**：不需要额外的记忆存储，自适应遗忘比记忆压缩更高效
- **权重量化友好**：自适应衰减可以在量化权重上运行
