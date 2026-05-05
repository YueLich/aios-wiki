---
title: "Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory"
arXiv: 2604.11544
date: 2026-04-13
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory

## 论文基本信息

- **作者**: Weixian Waylon Li, Jiaxin Zhang, Xianan Jim Yang, Tiejun Ma, Yiwen Guo
- **arXiv**: https://arxiv.org/abs/2604.11544
- **领域**: cs.CL


## 摘要

Structured memory representations such as knowledge graphs are central to autonomous agents and other long-lived systems. However, most existing approaches model time as discrete metadata, either sorting by recency (burying old-yet-permanent knowledge), simply overwriting outdated facts, or requiring an expensive LLM call at every ingestion step, leaving them unable to distinguish persistent facts from evolving ones. To address this, we introduce RoMem, a drop-in temporal knowledge graph module for structured memory systems, applicable to agentic memory and beyond. A pretrained Semantic Speed Gate maps each relation's text embedding to a volatility score, learning from data that evolving relations (e.g., "president of") should rotate fast while persistent ones (e.g., "born in") should remain stable. Combined with continuous phase rotation, this enables geometric shadowing: obsolete facts are rotated out of phase in complex vector space, so temporally correct facts naturally outrank contradictions without deletion. On temporal knowledge graph completion, RoMem achieves state-of-the-art results on ICEWS05-15 (72.6 MRR). Applied to agentic memory, it delivers 2-3x MRR and answer accuracy on temporal reasoning (MultiTQ), dominates hybrid benchmark (LoCoMo), preserves static memory with zero degradation (DMR-MSC), and generalises zero-shot to unseen financial domains (FinTMMBench).

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
