---
title: "MemReader: From Passive to Active Extraction for Long-Term Agent Memory"
arXiv: 2604.07877
date: 2026-04-09
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# MemReader: From Passive to Active Extraction for Long-Term Agent Memory

## 论文基本信息

- **作者**: Jingyi Kang, Chunyu Li, Ding Chen, Bo Tang, Feiyu Xiong, +1 more
- **arXiv**: https://arxiv.org/abs/2604.07877
- **领域**: cs.CL


## 摘要

Long-term memory is fundamental for personalized and autonomous agents, yet populating it remains a bottleneck. Existing systems treat memory extraction as a one-shot, passive transcription from context to structured entries, which struggles with noisy dialogue, missing references, and cross-turn dependencies, leading to memory pollution, low-value writes, and inconsistency. In this paper, we introduce the MemReader family for active long-term memory extraction in agent systems: MemReader-0.6B, a compact and cost-efficient passive extractor distilled for accurate and schema-consistent structured outputs, and MemReader-4B, an active extractor optimized with Group Relative Policy Optimization (GRPO) to make memory writing decisions. Under a ReAct-style paradigm, MemReader-4B explicitly evaluates information value, reference ambiguity, and completeness before acting, and can selectively write memories, defer incomplete inputs, retrieve historical context, or discard irrelevant chatter. Experiments on LOCOMO, LongMemEval, and HaluMem show that MemReader consistently outperforms existing extraction-based baselines. In particular, MemReader-4B achieves state-of-the-art performance on tasks involving knowledge updating, temporal reasoning, and hallucination reduction. These results suggest that effective agent memory requires not merely extracting more information, but performing reasoning-driven and selective memory extraction to build low-noise and dynamically evolving long-term memory. Furthermore, MemReader has been integrated into MemOS and is being deployed in real-world applications. To support future research and adoption, we release the models and provide public API access.

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
