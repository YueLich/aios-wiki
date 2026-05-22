---
title: "Predictive Associative Memory: Retrieval Beyond Similarity Through Temporal Co-occurrence"
arXiv: "2602.11322"
date: "2026-02-11"
tags: [agent-memory, memory-retrieval, associative-memory, temporal-co-occurrence]
reviewer: auto
source: arXiv RSS/API
---

# Predictive Associative Memory: Retrieval Beyond Similarity Through Temporal Co-occurrence

## 论文基本信息

- **arXiv ID**: 2602.11322
- **发表日期**: 2026-02-11
- **作者**: Jason Dury
- **方向**: Associative Memory, Memory Retrieval, Temporal Co-occurrence, JEPA
- **类别**: cs.LG, cs.AI, cs.IR, cs.NE

## 摘要

当前神经系统的记忆方法依赖相似度检索：给定查询，找到表示最相似的存储状态。这一假设——有用的记忆就是相似的记忆——忽视了生物记忆的一个根本特性：通过时间共现（temporal co-occurrence）进行关联记忆。本文提出 Predictive Associative Memory（PAM），一种基于 JEPA（Joint Embedding Predictive Architecture）风格的预测器架构，在连续经历流中通过时间共现进行训练，学会在嵌入空间的关联结构中导航。PAM 引入 Inward JEPA，对存储的经历进行操作（预测可联想关联的过去状态），作为标准 Outward JEPA（对输入感知数据操作、预测未来状态）的补充。在合成基准测试中，预测器的顶级检索有 97% 是真正的时序关联项；在余弦相似度为零的跨边界检索任务中，PAM 达到 Recall@20 = 0.421；在跨房间配对（嵌入相似度无信息量）中，预测器仍达到 AUC = 0.849（余弦相似度仅为 0.503）。

## 核心贡献

### 1. 打破"相似性=有用性"的假设

传统记忆检索依赖表示相似度，但生物记忆的关联机制远不止于此——两个记忆片段如果经常在时间上共同出现，它们之间就存在关联，即使它们的表示完全不相似。PAM 首次在神经记忆系统中形式化了这一关联机制。

### 2. Inward JEPA — 逆向预测的关联导航

**Outward JEPA**（标准组件）：对输入的感官数据操作，预测未来状态（下一时刻的表示）。

**Inward JEPA**（PAM 创新）：对存储的经历操作，预测在时间上可关联的过去状态。通过在"时间共现结构"上训练，Inward JEPA 学到了超越几何相似性的关联关系。

### 3. 时间共现作为关联信号

在合成基准测试中的对照实验：
- 预测器的 Association Precision@1 = 0.970（顶级检索 97% 是真正的时序关联）
- 跨边界 Recall@20 = 0.421（余弦相似度此时为零）
- 时间打乱控制组：打乱时间顺序后跨边界召回率下降 90%，证实信号来自真实的时间共现结构

### 4. 泛化能力的证明

即使在嵌入相似度完全无信息量的跨房间场景，PAM 依然达到 AUC = 0.849（随机猜测 0.5，余弦相似度 0.503），说明学到的关联是真正的时间共现模式，而非嵌入几何的副产品。

## 为什么重要

这篇论文从认知科学角度切入，提出了一个根本性的改进方向：记忆检索不应该只依赖"相似性"，还应该依赖"时间共现"。这对现有的 RAG 和记忆系统是一个重要补充——很多有用的记忆关联恰恰来自共同经历，而非语义相似。

## 与移动端/端侧的相关性

PAM 本身是一个轻量级的记忆检索架构，其 Inward/Outward JEPA 的设计理念对端侧记忆系统有启发：可以在边缘设备上存储时间共现图谱，通过小规模的预测器网络实现高效关联检索，无需大规模向量数据库。

## 参考文献

（参考文献待从原文补充）
