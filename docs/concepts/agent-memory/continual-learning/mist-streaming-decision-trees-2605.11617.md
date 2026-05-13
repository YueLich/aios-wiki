---
title: "MIST: Reliable Streaming Decision Trees for Online Class-Incremental Learning via McDiarmid Bound"
arXiv: 2605.11617
date: 2026-05-12
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# MIST: Reliable Streaming Decision Trees for Online Class-Incremental Learning via McDiarmid Bound

**作者**: Phu-Hoa Pham, Chi-Nguyen Tran, Nguyen Lam Phu Quy, Dao Sy Duy Minh, Huynh Trung Kiet, Long Tran-Thanh  
**发表**: 2026-05-12  
**方向**: 持续学习  
**类别**: cs.LG

## 摘要

流决策树是开放世界持续学习的天然候选者，因为它们执行局部更新、享有有界内存且具有静态决策边界。尽管有这些优势，它们在在线类别增量学习（online class-incremental learning）中仍然失效，原因是两种耦合的校准失败：(i) 随着类别数 K 扩展，其分裂准则变得不可靠；(ii) 分裂时缺乏知识迁移。这两种失败有一个共同根源：信息增益的范围本质上随 log2 K 缩放。因此，任何从中推导出的 Hoeffding 风格置信半径必然随类别数增长，使得与 K 无关的分裂准则在结构上不可能，从而剥夺了将流决策树应用于持续学习的潜在益处。为解决这一问题，本文提出 MIST（McDiarmid Incremental Streaming Tree），通过三个集成组件解决这两种失败：(i) 一个针对 Gini 分裂的紧密、K 无关的 McDiarmid 置信半径，作为结构正则化器；(ii) 贝叶斯继承协议，通过截断高斯矩将父节点统计量投影到子节点，在分裂最保守时提供最强的方差缩减保证；(iii) 每叶 KLL 分位数草图，支持从单一数据结构进行连续阈值评估和几何自适应叶预测。在标准和压力测试表格流上，MIST 在近高斯基准上具有竞争力，在非高斯几何上唯一鲁棒——而 SOTA 基准在此崩溃。

## 核心贡献

1. **K 无关 McDiarmid 置信半径**：为 Gini 分裂提出紧密的、与类别数无关的 McDiarmid 置信半径，作为结构正则化器，解决信息增益范围随 log2 K 缩放的根本问题。
2. **贝叶斯继承协议**：通过截断高斯矩将父节点统计量投影到子节点，分裂最保守时提供最强方差缩减保证。
3. **KLL 分位数草图**：每叶 KLL 分位数草图支持连续阈值评估和几何自适应叶预测，从单一数据结构同时实现两者。
4. **理论与实验验证**：在标准表格流和压力测试场景下，MIST 在近高斯基准上具有竞争力，在 SOTA 基准崩溃的非高斯几何上唯一保持鲁棒。

## 为什么重要

持续学习中的灾难性遗忘问题在流学习场景下尤为棘手——模型需要在只见过一次的数据上进行增量更新。现有方法在高类别数下因信息增益置信半径过大而失效。MIST 通过严格的 McDiarmid 界分析，首次实现了与类别数无关的分裂准则，为开放世界持续学习提供了理论严格且实践有效的解决方案。

## 与移动端/端侧的相关性

流决策树天然适合端侧资源受限场景：局部更新、有界内存、无需存储完整历史数据。MIST 的几何自适应叶预测能力使其能够在非高斯数据分布上保持鲁棒，这对于移动端多变的实际数据分布尤为重要。

## 参考文献

- 原论文: arXiv:2605.11617
