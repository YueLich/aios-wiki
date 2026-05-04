---
title: "NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning"
arXiv: 2604.27031
date: 2026-04-29
tags: [continual-learning, neurogenesis, stability-plasticity, resource-adaptation]
reviewer: auto
source: arXiv RSS/API
---

# NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning

## 论文基本信息

- **arXiv ID**: 2604.27031
- **作者**: (From paper)
- **提交日期**: 2026-04-29
- **类别**: cs.LG, cs.AI, cs.NE

## 摘要

In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space. Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture sized for this unknown future. When tasks are only weakly related, fixed architectures progressively run out of plastic resources; when tasks are few or strongly overlapping, models are often over-provisioned. Inspired by neurogenesis in biology, we propose NORACL to address the stability-plasticity dilemma by tackling the oracle architecture problem through neuronal growth. Starting from a compact network, NORACL grows only when needed by monitoring two complementary signals for representational and plasticity saturation. We evaluate NORACL against oracle-sized static baselines across varying task counts and geometries. Across all settings, NORACL achieves final average accuracies that are better than or on par with oracle-provisioned static baselines while using fewer parameters.

## 核心贡献

1. **神经生成启发式 CL**：受生物神经发生启发，通过神经元生长解决稳定性-可塑性困境。
2. **自适应容量增长**：仅在需要时增长（监控表征饱和度和可塑性饱和度），无需预设任务数量。
3. **无需 Oracle 基线**：相比固定容量架构，NORACL 可以与 Oracle 规模的静态基线持平或更优，同时使用更少参数。
4. **可解释性增长模式**：不相似任务扩展特征提取层；相似任务向后期特征融合层偏移。

## 为什么重要

持续学习的核心困境在于：我们不知道未来会遇到多少任务、任务之间有多少重叠。固定容量架构要么在弱相关任务下耗尽可塑性资源，要么在任务少或强重叠时过度配置。NORACL 通过自适应神经元生长解决这个 Oracle 问题，是持续学习架构设计的重要进展。在所有测试设置中均达到或超过 Oracle 基线性能，同时参数更少。

## 与移动端/端侧相关性

- 移动端 Agent 面临未知任务流：用户可能随时安装新 App、使用新功能
- 自适应增长减少内存占用——仅在需要时扩展，与移动端资源约束天然契合
- 无需预先知道任务数量对开放世界移动助手尤为重要
- 可解释性增长模式（不相似任务扩展不同层）对理解移动端学习行为有价值
