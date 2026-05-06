---
title: "When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry"
arXiv: 2604.27656
date: 2026-04-27
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# When Does Structure Matter in Continual Learning? Dimensionality Controls When Modularity Shapes Representational Geometry

## 论文基本信息

- **作者**: Kathrin Korte, Joachim Winter Pedersen, Eleni Nisioti
- **arXiv**: https://arxiv.org/abs/2604.27656
- **领域**: cs.LG, cs.NE

## 摘要

持续学习系统必须在新知识获取（可塑性）和已有知识保留（稳定性）之间取得平衡。这一平衡影响跨任务的知识复用：共享结构在任务相似时支持迁移，但当新学习干扰已有表示时也会引发干扰。论文研究维度在这一动态中的作用，发现维度决定了模块化何时塑造表示几何——低维时模块化促进稳定知识保留，高维时模块化反而可能损害跨任务迁移。

## 核心贡献

1. **Dimensionality × Modularity 交互**: 首次系统研究维度在 CL 中模块化效果的作用
2. **Dimension-dependent 机制**: 低维和高维下模块化对表示几何的不同影响
3. **Practical Guidelines**: 为不同维度场景选择合适的 CL 策略提供实证指导
4. **Representation Geometry Analysis**: 通过表示几何分析解释模块化效果
5. **LoCoMo Benchmark 验证**: 在混合模态基准上验证发现

## 研究背景与问题

模块化（modular）架构被广泛认为有利于持续学习，但实证结果不一致。论文发现这源于维度的影响被忽视——模块化在低维和高维场景下有截然不同的效果。

## 核心方法

1. **Synthetic Continual Learning Suite**: 控制维度、任务相似度、模块化的受控 CL 环境
2. **Representation Geometry Metrics**: 量化表示空间中任务结构的保持程度
3. **Dimensionality Scaling**: 在 16D 到 4096D 范围内系统性变化维度
4. **Module Responsibility Analysis**: 分析每个模块对不同任务的响应模式

## 为什么重要

该研究揭示了 CL 中一个以前被忽视但至关重要的变量——维度。为 CL 方法的设计和选择提供了新的理论视角：没有普适最优模块化策略，维度决定策略选择。

## 与移动端/端侧相关性

1. **移动端维度约束**: 移动端模型通常维度较低（参数量小），模块化策略更有效
2. **资源受限设计**: 根据目标设备维度选择合适的 CL 策略
3. **嵌入式系统**: 嵌入式 AI 系统的固定资源预算下，维度是设计决策的关键参数
