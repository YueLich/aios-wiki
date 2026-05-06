---
title: "MPCS: Neuroplastic Continual Learning via Multi-Component Plasticity and Topology-Aware EWC"
arXiv: 2605.02509
date: 2026-05-04
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# MPCS: Neuroplastic Continual Learning via Multi-Component Plasticity and Topology-Aware EWC

**作者:** Joern Hentsch
**发表:** 2026-05-04

## 摘要

Continual learning systems face a fundamental tension between plasticity -- acquiring new knowledge -- and stability -- retaining prior knowledge. We introduce MPCS (Multi-Plasticity Continual System), a neuroplastic architecture that integrates eleven complementary mechanisms: task-driven neurogenesis, Fourier-encoded inputs, EWC regularization, meta-replay, mixed consolidation, hybrid gating, synapse pruning/regeneration, Hebbian updates, task similarity routing, adaptive growth control, and continuous neuron importance tracking. We evaluate MPCS on MEP-BENCH, a multi-track benchmark spanning 31 tasks across regression, classification, logic, and mixed domains, using a three-dimensional Pareto criterion over task performance (Perf), representation diversity (RD), and gradient conflict rate (GCR).

## 核心贡献

1. **十一机制神经塑性架构**: 系统整合了 11 种互补的可塑性机制，包括神经发生、傅里叶编码、EWC 正则化、meta-replay、混合巩固、混合门控、突触剪枝/再生、Hebbian 更新等
2. **MEP-BENCH 多维基准**: 跨 31 个任务的多元基准，使用三维 Pareto 标准（Perf、RD、GCR）评估
3. **拓扑感知 EWC**: 发现全局 EWC 有害（NES = -4.2），拓扑局部 EWC 可以缓解但不能消除；存在单调关系：global EWC < topology EWC < no EWC
4. **Pareto 前沿作为模型压缩指南**: 移除 EWC + Hebbian 联合产生 MPCS_EFFICIENT，以 4.7x 更低计算成本（127 vs 602 分钟）提升 Perf 0.6 pp

## 关键发现

- Fourier 编码是最关键的单组件（移除导致 Perf 下降 30.7 pp，MEP gate 失败率 14%）
- EWC 类正则化在持续学习中并非总是有效——存在任务相似度 regime 依赖
- Pareto 状态评估具有预测性，可作为可操作模型压缩指南

## 为什么重要

首次在统一框架下系统评估了 11 种互补的神经塑性机制，并揭示了它们之间的相互作用和 trade-off。这对于设计能够同时保持稳定性和可塑性的端侧持续学习系统有重要指导意义。

## 与端侧/移动端的相关性

MPCS 的发现对端侧持续学习有直接价值：Fourier 编码的极端重要性和 EWC 类正则化的 regime 依赖，提示端侧记忆系统应优先考虑输入编码优化而非复杂正则化。MPCS_EFFICIENT 的发现（移除 EWC + Hebbian）表明简化设计可能对端侧更有效。
