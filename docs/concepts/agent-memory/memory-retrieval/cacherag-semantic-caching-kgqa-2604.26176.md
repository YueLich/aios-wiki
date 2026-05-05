---
title: "CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering"
arXiv: 2604.26176
date: 2026-04-28
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering

## 论文基本信息

- **作者**: Yushi Sun, Lei Chen
- **arXiv**: https://arxiv.org/abs/2604.26176
- **领域**: cs.DB


## 摘要

The integration of Large Language Models (LLMs) with Retrieval-Augmented Generation (RAG) has significantly advanced Knowledge Graph Question Answering (KGQA). However, existing LLM-driven KGQA systems act as stateless planners, generating retrieval plans in isolation without exploiting historical query patterns: analogous to a database system that optimizes every query from scratch without a plan cache. This fundamental design flaw leads to schema hallucinations and limited retrieval coverage. We propose CacheRAG, a systematic cache-augmented architecture for LLM-based KGQA that transforms stateless planners into continual learners. Unlike traditional database plan caching (which optimizes for frequency), CacheRAG introduces three novel design principles tailored for LLM contexts: (1) Schema-agnostic user interface: A two-stage semantic parsing framework via Intermediate Semantic Representation (ISR) enables non-expert users to interact purely in natural language, while a Backend Adapter grounds the LLM with local schema context to compile executable physical queries safely. (2) Diversity-optimized cache retrieval: A two-layer hierarchical index (Domain $\rightarrow$ Aspect) coupled with Maximal Marginal Relevance (MMR) maximizes structural variety in cached examples, effectively mitigating reasoning homogeneity. (3) Bounded heuristic expansion: Deterministic depth and breadth subgraph operators with strict complexity guarantees significantly enhance retrieval recall without risking unbounded API execution. Extensive experiments on multiple benchmarks demonstrate that CacheRAG significantly outperforms state-of-the-art baselines (e.g., +13.2% accuracy and +17.5% truthfulness on the CRAG dataset).

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
