---
title: "Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory"
arXiv: 2604.11544
date: 2026-04-13
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# RoMem: Time is Not a Label — Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory

## 论文基本信息

- **作者**: Yi Li, et al.
- **arXiv**: https://arxiv.org/abs/2604.11544
- **领域**: cs.AI, cs.KG

## 摘要

结构化记忆表示（如知识图谱）是自主 Agent 和其他长寿系统的核心。但现有方法将时间建模为离散元数据——按时间排序（埋没旧有永久知识）、直接覆盖过时事实，或在每次摄入时调用昂贵的 LLM——无法区分持久事实和演化事实。RoMem 引入连续相位旋转（continuous phase rotation），将时间引入几何向量空间。通过预训练的语义速度门控（Semantic Speed Gate）映射每个关系文本嵌入到波动性分数，学习哪些关系应该快速旋转（如"president of"），哪些应该保持稳定（如"born in"）。结合连续相位旋转，过时事实在复杂向量空间中旋转出相位，使时间正确的事实自然排名高于矛盾。新事实无需显式删除旧事实。在时序知识图谱补全上，RoMem 在 ICEWS05-15 上达到 72.6 MRR。

## 核心贡献

1. **Continuous Phase Rotation**: 将时间建模为连续相位旋转，而非离散元数据
2. **Semantic Speed Gate**: 预训练网络学习每个关系类型的波动性
3. **Geometric Shadowing**: 几何阴影机制使过时事实在向量空间中自动淡出
4. **No Explicit Deletion**: 新事实无需显式删除旧事实，通过相位分离实现
5. **State-of-the-art**: 时序 KG 补全在 ICEWS05-15 上达到 72.6 MRR

## 研究背景与问题

现有知识图谱和时间建模方法将时间当作标签或过滤器，无法捕捉事实的时间演化本质。Agent 记忆中的"zombie memories"（过时但未被删除的事实）是一个核心挑战。

## 核心方法

1. **Temporal Knowledge Graph Module**: 可插入式时序 KG 模块
2. **Semantic Speed Gate**: 预训练网络预测每个关系类型的波动性分数
3. **Phase Rotation**: 在复数向量空间中执行连续相位旋转
4. **Geometric Shadowing**: 过时事实旋转出有效相位范围
5. **Agentic Memory Integration**: 与 Agent 记忆系统无缝集成

## 为什么重要

RoMem 为 Agent 记忆系统提供了一种优雅的时间建模机制。过时事实通过几何机制自然"淡出"，而非通过显式删除。这对构建长期运行的 Agent 记忆系统有重要价值。

## 与移动端/端侧相关性

1. **可插入模块**: RoMem 是可插入 Agent 记忆系统的模块，适合端侧部署
2. **无需显式遗忘**: 几何机制自动处理过时信息，降低端侧管理复杂度
3. **资源高效**: 不需要 LLM 调用，时序推理在向量空间高效执行
4. **时序推理**: 对需要时间推理的移动端 Agent（如日程、位置历史）有直接价值
