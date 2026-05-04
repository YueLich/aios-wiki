---
title: CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering
arXiv: 2604.26176
date: 2026-04-28
tags: [agent-memory, memory_retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.26176
- **作者**: Yushi Sun, Lei Chen
- **提交日期**: 2026-04-28

## 摘要

The integration of Large Language Models (LLMs) with Retrieval-Augmented Generation (RAG) has significantly advanced Knowledge Graph Question Answering (KGQA). However, existing LLM-driven KGQA systems act as stateless planners, generating retrieval plans in isolation without exploiting historical query patterns: analogous to a database system that optimizes every query from scratch without a plan cache. This fundamental design flaw leads to schema hallucinations and limited retrieval coverage.

We propose CacheRAG, a systematic cache-augmented architecture for LLM-based KGQA that transforms stateless query planning into a cache-aware paradigm. CacheRAG maintains a multi-level semantic cache that captures historical query patterns, plans, and retrieval results, enabling reuse of computation across related queries.

The key insight is that KGQA queries exhibit significant temporal and structural locality: users tend to ask about related entities and relationships within a session. By exploiting this locality, CacheRAG reduces redundant LLM calls, improves retrieval consistency, and mitigates schema hallucinations through cached plan reuse.

Experiments on standard KGQA benchmarks demonstrate significant improvements in both efficiency (reduced LLM calls) and accuracy (mitigated hallucinations) compared to stateless baselines.

## 核心贡献

1. **问题定义**: CacheRAG 针对 memory retrieval 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 memory、retrieval 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
