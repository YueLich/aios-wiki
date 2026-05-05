---
title: "CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering"
arXiv: 2604.26176
date: 2026-04-28
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering

**作者:** Yushi Sun, Lei Chen
**发表:** 2026-04-28

## 摘要

The integration of Large Language Models (LLMs) with Retrieval-Augmented Generation (RAG) has significantly advanced Knowledge Graph Question Answering (KGQA). However, existing LLM-driven KGQA systems act as stateless planners, generating retrieval plans in isolation without exploiting historical query patterns: analogous to a database system that optimizes every query from scratch without a plan cache. This fundamental design flaw leads to schema hallucinations and limited retrieval coverage. We propose CacheRAG, a systematic cache-augmented architecture for LLM-based KGQA that transforms stateless planners into continual learners. Unlike traditional database plan caching (which optimizes for frequency), CacheRAG introduces three novel design principles tailored for LLM contexts: (1) Schema-agnostic user interface: A two-stage semantic parsing framework via Intermediate Semantic Representation (ISR) enables non-expert users to interact purely in natural language, while a Backend Adapter grounds the LLM with local schema context to compile executable physical queries safely. (2) Diversity-optimized cache retrieval: A two-layer hierarchical index (Domain → Aspect) coupled with Maximal Marginal Relevance (MMR) maximizes structural variety in cached examples, effectively mitigating reasoning homogeneity. (3) Bounded heuristic expansion: Deterministic depth and breadth subgraph operators with strict complexity guarantees significantly enhance retrieval recall without risking unbounded API execution. Extensive experiments on multiple benchmarks demonstrate that CacheRAG significantly outperforms state-of-the-art baselines (e.g., +13.2% accuracy and +17.5% truthfulness on the CRAG dataset).

## 核心贡献

1. **CacheRAG 架构**: 首个将语义缓存引入 LLM-based KGQA 的系统，将 stateless planner 转变为持续学习者
2. **Schema-agnostic Interface**: 两阶段语义解析（ISR）让非专业用户用自然语言交互，后端适配器确保安全执行
3. **Diversity-optimized Cache**: 双层层级索引（Domain → Aspect）+ MMR（最大边际相关性），最大化推理多样性
4. **Bounded Heuristic Expansion**: 确定性深度/广度子图操作器，带严格复杂度保证，提升召回率
5. **性能提升**: CRAG 数据集上 +13.2% 准确率，+17.5% 真实性

## 为什么重要

LLM-based KGQA 系统长期面临 schema hallucination（生成计划时幻觉schema）和 retrieval coverage 不足的问题。CacheRAG 借鉴数据库系统的 plan cache 思想，首次为 LLM-driven KGQA 引入记忆缓存机制。与传统数据库缓存（优化频率）不同，CacheRAG 的缓存针对 LLM 上下文优化——强调多样性而非频率，从而避免重复同质化推理。这为 Agent 记忆系统的缓存设计提供了重要参考。

## 与端侧/移动端相关性

1. **层级索引结构（Domain → Aspect）** 适合端侧资源受限场景——两级缓存比全量扫描更高效
2. **Bounded expansion** 保证计算资源有上限，适合移动端/嵌入式部署
3. **自然语言接口（ISR）** 对端侧 Agent 的自然语言记忆查询有直接参考价值
4. 记忆缓存可显著减少对远程 KGQA API 的调用次数，降低延迟和带宽消耗

## 关键文献

- CRAG dataset
- Intermediate Semantic Representation (ISR)
- Maximal Marginal Relevance (MMR)
