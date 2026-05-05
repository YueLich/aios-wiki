---
title: "SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval"
arXiv: 2604.02431
date: 2026-04-02
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval

**作者:** Matthew McKee
**发表:** 2026-04-02

## 摘要

Retrieving relevant past interactions from long-term conversational memory typically relies on large dense retrieval models (110M-1.5B parameters) or LLM-augmented indexing. We introduce SelRoute, a framework that routes each query to a specialized retrieval pipeline -- lexical, semantic, hybrid, or vocabulary-enriched -- based on its query type. On LongMemEval_M, SelRoute achieves Recall@5 of 0.800 with bge-base-en-v1.5 (109M parameters) and 0.786 with bge-small-en-v1.5 (33M parameters), compared to 0.762 for Contriever with LLM-generated fact keys. A zero-ML baseline using SQLite FTS5 alone achieves NDCG@5 of 0.692, already exceeding all published baselines on ranking quality.

## 核心貢獻

1. **SelRoute 框架**: 根据查询类型将请求路由到专门的检索管道（词汇、语义、混合或词汇丰富化）
2. **Query Type Routing**: 首次在对话记忆检索中引入类型感知路由，根据查询特点选择最优检索策略
3. **轻量化检索**: 使用 33M 参数的小型模型达到与大型模型相当的召回率
4. **SQLite FTS5 Baseline**: 纯词法检索的零机器学习基线即可超过所有已发布的基线
5. **混合管道设计**: 支持 lexical、semantic、hybrid、vocabulary-enriched 四种检索模式

## 為什麼重要

长期对话记忆检索通常依赖大型密集检索模型（110M-1.5B 参数），计算成本高。SelRoute 通过查询类型路由，用小模型（33M 参数）实现与大型模型相当的检索质量，显著降低了端侧部署的计算成本。零机器学习的 SQLite FTS5 基线即可超过已发布基线，说明词法检索在对话记忆场景中被低估了。

## 與端側/移動端相關性

1. **轻量化检索**: 33M 参数模型适合端侧移动设备
2. **查询类型路由**: 根据查询动态选择检索策略，优化资源分配
3. **SQLite FTS5 支持**: 本地数据库即可实现高质量检索，无需云端 API
4. **降低推理成本**: 小模型显著减少内存占用和推理延迟
