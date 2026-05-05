---
title: "Memory-Augmented LLM-based Multi-Agent System for Automated Feature Generation on Tabular Data"
arXiv: 2604.20261
date: 2026-04-14
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Fengxian Dong, Zhi Zheng, Xiao Han, Wei Chen, Jingqing Ruan, Tong Xu, Yong Chen, Enhong Chen
- **提交日期**: 2026-04-14

## 摘要

Automated feature generation extracts informative features from raw tabular data without manual intervention and is crucial for accurate, generalizable machine learning. This paper proposes a multi-agent system where different agents specialize in different feature generation strategies, coordinated by a shared memory system. The memory stores previously generated features, their performance on different datasets, and the data characteristics they were effective for. When generating features for a new dataset, agents query memory to retrieve similar historical contexts and their successful feature patterns. Different agents handle different modalities: one generates statistical aggregates, another creates interaction features, a third handles temporal patterns.

## 核心贡献

1. **多 Agent 特征生成**: 不同 Agent 专精不同特征策略（统计聚合、交互特征、时序模式）
2. **跨数据集记忆迁移**: 存储历史特征效果，检索相似数据集的成功模式
3. **嵌入空间记忆组织**: 类似数据上下文在嵌入空间聚集

## 为什么重要

展示了记忆如何实现跨数据集的知识迁移，对于数据稀缺的边缘场景特别有价值。

## 与端侧/移动端的相关性

特征生成记忆可用于端侧数据稀缺场景（如个性化健康监测），通过相似用户数据的记忆迁移弥补本地数据不足。
