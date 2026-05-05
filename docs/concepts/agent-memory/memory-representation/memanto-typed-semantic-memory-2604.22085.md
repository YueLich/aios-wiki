---
title: "Memanto: Typed Semantic Memory with Information-Theoretic Retrieval for Long-Horizon Agents"
arXiv: 2604.22085
date: 2026-04-23
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# Memanto: Typed Semantic Memory with Information-Theoretic Retrieval for Long-Horizon Agents

## 论文基本信息

- **作者**: Seyed Moein Abtahi, Rasa Rahnema, Hetkumar Patel, Neel Patel, Majid Fekri, +1 more
- **arXiv**: https://arxiv.org/abs/2604.22085
- **领域**: cs.AI
- **备注**: 13 Pages, 10 Tables, 8 Figures

## 摘要

The transition from stateless language model inference to persistent, multi session autonomous agents has revealed memory to be a primary architectural bottleneck in the deployment of production grade agentic systems. Existing methodologies largely depend on hybrid semantic graph architectures, which impose substantial computational overhead during both ingestion and retrieval. These systems typically require large language model mediated entity extraction, explicit graph schema maintenance, and multi query retrieval pipelines. This paper introduces Memanto, a universal memory layer for agentic artificial intelligence that challenges the prevailing assumption that knowledge graph complexity is necessary to achieve high fidelity agent memory. Memanto integrates a typed semantic memory schema comprising thirteen predefined memory categories, an automated conflict resolution mechanism, and temporal versioning. These components are enabled by Moorcheh's Information Theoretic Search engine, a no indexing semantic database that provides deterministic retrieval within sub ninety millisecond latency while eliminating ingestion delay. Through systematic benchmarking on the LongMemEval and LoCoMo evaluation suites, Memanto achieves state of the art accuracy scores of 89.8 percent and 87.1 percent respectively. These results surpass all evaluated hybrid graph and vector based systems while requiring only a single retrieval query, incurring no ingestion cost, and maintaining substantially lower operational complexity. A five stage progressive ablation study is presented to quantify the contribution of each architectural component, followed by a discussion of the implications for scalable deployment of agentic memory systems.

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
