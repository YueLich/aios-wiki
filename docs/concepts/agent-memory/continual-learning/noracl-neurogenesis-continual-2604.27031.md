---
title: NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning
arXiv: 2604.27031
date: 2026-04-29
tags: [agent-memory, continual_learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.27031
- **作者**: Karthik Charan Raghunathan, Christian Metzner, Laura Kriener, Melika Payvand
- **提交日期**: 2026-04-29

## 摘要

In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space.

Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture size. We take a different approach, drawing inspiration from adult neurogenesis in the hippocampus: the continuous addition of new neurons provides fresh representational capacity for novel inputs without overwriting existing memories.

NORACL introduces resource-adaptive neurogenesis where new network modules are dynamically instantiated when novelty is detected, but only after existing resources are proven insufficient. This oracle-free approach eliminates the need to know task count or overlap in advance. The system identifies novelty through divergence monitoring in activation space, triggering module instantiation only when truly necessary.

Experiments on sequential task benchmarks show that NORACL achieves performance competitive with oracle methods while requiring no prior knowledge of the task stream, demonstrating that neurogenesis-inspired resource allocation is a viable path to truly autonomous continual learning.

## 核心贡献

1. **问题定义**: NORACL 针对 continual learning 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 continual、learning 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
