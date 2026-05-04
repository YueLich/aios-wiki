---
title: "Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory"
arXiv: 2604.11544
date: 2026-04-13
authors: ["Weixian Waylon Li et al."]
tags: [agent-memory, memory-representation, temporal-knowledge-graph, knowledge-graph, time-modeling]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.11544
- **作者**: Weixian Waylon Li, Jiaxin Zhang, Xianan Jim Yang et al.
- **提交日期**: 2026-04-13
- **方向**: 时序知识图谱 / Agent 记忆 / 时间建模

## 摘要（全文翻译）

知识图谱等结构化记忆表示对自主 Agent 和其他长期运作系统至关重要。然而现有方法将时间建模为离散元数据：按近因性排序（埋没旧有但永久的知识）、简单覆盖过时事实，或在每次摄取步骤需要昂贵的 LLM 调用，无法区分持久事实和演化事实。

本文提出 **RoMem**，一个用于结构化记忆系统的即插即用时序知识图谱模块，适用于 Agent 记忆等场景。预训练的语义速度门（Semantic Speed Gate）将每个关系文本嵌入映射到波动性分数，学习哪些关系应该快速旋转（如"president of"），哪些应该保持稳定（如"born in"）。结合连续相位旋转，实现了几何阴影（geometric shadowing）：过时事实在复向量空间中旋转出相位，使时间正确的事实自然优先于过时事实。

## 核心贡献

1. **连续相位旋转**：将时间建模为连续的相位旋转，而非离散标签或简单覆盖
2. **语义速度门**：预训练模型学习关系的固有波动性，区分"常变"和"永久"关系
3. **几何阴影**：过时事实在向量空间中被"遮蔽"，无需显式删除
4. **即插即用模块**：可叠加在现有 Agent 记忆系统之上

## 为什么重要

时间建模是知识图谱和 Agent 记忆的长期难题。RoMem 的几何方法优雅地解决了三个常见问题：旧永久知识被埋没、过时事实被覆盖、需要 LLM 调用判断时间属性。相位旋转提供了一种无需 LLM 的、几何化的时间建模方案。

## 与端侧/移动端的相关性

RoMem 是端侧友好的：一旦语义速度门预训练完成，判断关系是否过时只需要向量运算，无需 LLM 调用。即插即用的设计意味着可以在现有记忆系统上叠加时序建模能力。
