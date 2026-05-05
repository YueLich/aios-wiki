---
title: "SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval"
arXiv: 2604.02431
date: 2026-04-02
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval

## 论文基本信息

- **作者**: Matthew McKee
- **arXiv**: https://arxiv.org/abs/2604.02431
- **领域**: cs.IR
- **备注**: 12 pages, 12 tables, 3 appendices

## 摘要

Retrieving relevant past interactions from long-term conversational memory typically relies on large dense retrieval models (110M-1.5B parameters) or LLM-augmented indexing. We introduce SelRoute, a framework that routes each query to a specialized retrieval pipeline -- lexical, semantic, hybrid, or vocabulary-enriched -- based on its query type. On LongMemEval_M (Wu et al., 2024), SelRoute achieves Recall@5 of 0.800 with bge-base-en-v1.5 (109M parameters) and 0.786 with bge-small-en-v1.5 (33M parameters), compared to 0.762 for Contriever with LLM-generated fact keys. A zero-ML baseline using SQLite FTS5 alone achieves NDCG@5 of 0.692, already exceeding all published baselines on ranking quality -- a gap we attribute partly to implementation differences in lexical retrieval. Five-fold stratified cross-validation confirms routing stability (CV gap of 1.3-2.4 Recall@5 points; routes stable for 4/6 query types across folds). A regex-based query-type classifier achieves 83% effective routing accuracy, and end-to-end retrieval with predicted types (Recall@5 = 0.689) still outperforms uniform baselines. Cross-benchmark evaluation on 8 additional benchmarks spanning 62,000+ instances -- including MSDialog, LoCoMo, QReCC, and PerLTQA -- confirms generalization without benchmark-specific tuning, while exposing a clear failure mode on reasoning-intensive retrieval (RECOR Recall@5 = 0.149) that bounds the claim. We also identify an enrichment-embedding asymmetry: vocabulary expansion at storage time improves lexical search but degrades embedding search, motivating per-pipeline enrichment decisions. The full system requires no GPU and no LLM inference at query time.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
