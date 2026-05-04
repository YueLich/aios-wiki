---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-30
authors: "Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti, Sebastian Risi (IT University of Copenhagen)"
tags: [agent-memory, continual-learning, modularity, dimensionality, representational-geometry]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2604.27656v1
- **发表**: 2026-04-30
- **作者**: Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti, Sebastian Risi (ITU Copenhagen)
- **方向**: 持续学习 / 网络架构
- **开源**: 待确认

---

## 核心问题

**网络架构（模块化 vs 单模块）在持续学习中何时重要？**

直觉告诉我们模块化应该有帮助，但实证结果时好时坏——这个论文揭示了**条件**。

---

## 三个关键变量

### 1. 任务相似性

- Low（低相似）
- Medium（中相似）
- High（高相似）

### 2. 权重初始化规模

通过调整初始化规模，诱导出不同的**有效表征维度**：
- 大初始化 → 高维表征空间（未约束）
- 小初始化 → 低维/rich表征空间（紧凑）

### 3. 表征维度 Regime

| Regime | 表征空间 | 架构影响 |
|---|---|---|
| **高维** | 充足，未约束 | 架构影响最小 |
| **低维 (rich)** | 受限，紧凑 | 架构分离是决定性的 |

---

## 核心发现

### 高维 Regime（充足未约束表征）

> Architecture has minimal impact when representations are sufficiently unconstrained to accommodate multiple tasks without strong interference.

系统有足够空间容纳多任务而不产生强干扰，模块化/单模块差异消失。

### 低维 Regime（表征空间受限）

> In lower-dimensional (rich) regimes, architectural separation is decisive.

模块化架构的优势在紧凑表征下完全显现——任务分区可以强制隔离表征冲突。

### 任务相似性的调节作用

| 任务相似性 | 共享结构 | 分离结构 |
|---|---|---|
| **高相似** | 支持迁移（shared representations help） | 可能浪费容量 |
| **低相似** | 干扰（shared → interference） | 隔离更好 |

---

## 为什么重要

从**表征几何(representational geometry)**角度解释了模块化何时有效的条件。这是对"为什么之前的模块化持续学习工作结果不一致"的最清晰回答。

### 与移动端/端侧的相关性

端侧场景通常：
- 需要**低维紧凑表征**（内存/计算受限）
- 任务相对**多样化**（不同用户场景）

这意味着**端侧持续学习几乎必然需要模块化架构**——和高维服务器端场景完全不同。

---

## 实验范式

参考了经典的 **Transfer–Interference Studies**（追溯到 1960s 的心理学实验），用现代深度网络复现了"模块化如何帮助/伤害持续学习"的核心机制。
