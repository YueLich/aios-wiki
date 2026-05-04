---
title: "NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning"
arXiv: 2604.27031
date: 2026-04-29
authors: ["Karthik Charan Raghunathan", "Christian Metzner", "Laura Kriener"]
tags: [agent-memory, continual-learning, neurogenesis, resource-adaptive, network-growth]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.27031
- **作者**: Karthik Charan Raghunathan, Christian Metzner, Laura Kriener
- **提交日期**: 2026-04-29
- **方向**: 持续学习 / 神经生成 / 资源适应

## 摘要（全文翻译）

持续学习设置中，模型需要足够的可塑性来学习新任务，同时足够稳定以不干扰已学能力。本文认为这个困境有**架构根源**：有限网络有有限的表示和可塑资源，而所需容量取决于未来任务流的属性——这些属性是未知的。

NORACL 提出了**神经生成（neurogenesis）**机制，动态添加新神经元来处理新任务，避免旧知识的覆盖。

## 核心贡献

1. **神经生成机制**：在网络中动态添加新神经元处理新任务，而非复用已用容量
2. **无 Oracle 的资源适应**：不需要预先知道有多少任务要来，动态适应
3. **稳定-可塑性的架构解决**：通过生长而非压缩解决稳定-可塑性困境

## 为什么重要

NORACL 直接解决了稳定-可塑性困境的**架构根源**：有限容量必然导致新知识覆盖旧知识。通过动态添加神经元，网络容量可以随任务数量扩展，理论上支持无限任务学习。

## 与端侧/移动端的相关性

神经生成对端侧持续学习有重要启示：固定容量的模型在任务数增长时必然面临遗忘，动态网络生长是一种根本性解决方案。但神经生成在标准硬件上的实现仍需大量研究。
