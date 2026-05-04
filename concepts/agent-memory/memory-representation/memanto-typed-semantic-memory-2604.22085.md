---
title: "Memanto: Typed Semantic Memory with Information-Theoretic Retrieval for Long-Horizon Agents"
arXiv: 2604.22085
date: 2026-04-23
tags: [agent-memory, memory-representation, semantic-memory, retrieval]
reviewer: auto
source: arXiv RSS/API
---

# Memanto: Typed Semantic Memory with Information-Theoretic Retrieval for Long-Horizon Agents

## 论文基本信息

- **arXiv ID**: 2604.22085
- **作者**: (From Memanto paper)
- **提交日期**: 2026-04-23
- **类别**: cs.CL, cs.AI

## 摘要

The transition from stateless language model inference to persistent, multi-session autonomous agents has revealed memory to be a primary architectural bottleneck in the deployment of production-grade agentic systems. Existing methodologies largely depend on hybrid semantic graph architectures, which impose substantial computational overhead during both ingestion and retrieval. These systems typically require large language model mediated entity extraction, explicit graph schema maintenance, and multi-query retrieval pipelines. This paper introduces Memanto, a universal memory layer for agentic artificial intelligence that challenges the prevailing assumption that knowledge graph complexity is necessary to achieve high-fidelity agent memory. Memanto integrates a typed semantic memory schema comprising thirteen predefined memory categories, an automated conflict resolution mechanism, and temporal versioning. These components are enabled by Moorcheh's Information Theoretic Search engine, a no-indexing semantic database that provides deterministic retrieval within sub-90-millisecond latency while eliminating ingestion delay. Through systematic benchmarking on the LongMemEval and LoCoMo evaluation suites, Memanto achieves state-of-the-art accuracy scores of 89.8% and 87.1% respectively. These results surpass all evaluated hybrid graph and vector-based systems while requiring only a single retrieval query, incurring no ingestion cost, and maintaining substantially lower operational complexity.

## 核心贡献

1. **Typed Semantic Memory Schema**：13个预定义记忆类别的类型化语义记忆模式，平衡抽象性与特异性。
2. **信息论检索引擎**：无索引语义数据库，实现确定性检索（sub-90ms延迟），消除摄取延迟。
3. **冲突解决机制**：自动化冲突解决 + 时间版本控制，支持记忆演化。
4. **极低操作复杂度**：单次检索查询即可完成，无需多查询管道。

## 为什么重要

Memanto 证明了实现高精度 Agent 记忆不一定需要复杂的知识图谱架构。通过类型化模式 + 信息论检索的组合，在 LongMemEval（89.8%）和 LoCoMo（87.1%）上均达到 SOTA，超越所有混合图+向量系统。这对资源受限的端侧部署意义重大——删除复杂的图谱维护可以显著降低计算和工程复杂度。

## 与移动端/端侧相关性

- 无索引检索架构非常适合端侧：减少知识图谱维护的 LLM 调用开销
- 13类预定义类别提供结构化记忆，与移动端 App 任务域契合
- Sub-90ms 延迟满足移动端实时性需求
- 低复杂度 pipeline 减少内存和计算足迹
