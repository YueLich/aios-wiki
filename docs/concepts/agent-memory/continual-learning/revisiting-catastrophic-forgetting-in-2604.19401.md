---
title: "Revisiting Catastrophic Forgetting in Continual Knowledge Graph Embedding"
arXiv: 2604.19401
date: 2026-04-21
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Revisiting Catastrophic Forgetting in Continual Knowledge Graph Embedding

## 论文基本信息

- **作者**: Gerard Pons, Carlos Escolano, Besim Bilalli, Anna Queralt
- **arXiv**: https://arxiv.org/abs/2604.19401
- **领域**: cs.LG
- **备注**: Pre-print submitted

## 摘要

Knowledge Graph Embeddings (KGEs) support a wide range of downstream tasks over Knowledge Graphs (KGs). In practice, KGs evolve as new entities and facts are added, motivating Continual Knowledge Graph Embedding (CKGE) methods that update embeddings over time. Current CKGE approaches address catastrophic forgetting (i.e., the performance degradation on previously learned tasks) primarily by limiting changes to existing embeddings.   However, we show that this view is incomplete. When new entities are introduced, their embeddings can interfere with previously learned ones, causing the model to predict them in place of previously correct answers. This phenomenon, which we call entity interference, has been largely overlooked and is not accounted for in current CKGE evaluation protocols. As a result, the assessment of catastrophic forgetting becomes misleading, and CKGE methods performance is systematically overestimated.   To address this issue, we introduce a corrected CKGE evaluation protocol that accounts for entity interference. Through experiments on multiple benchmarks, we show that ignoring this effect can lead to performance overestimation of up to 25%, particularly in scenarios with significant entity growth. We further analyze how different CKGE methods and KGE models are affected by the different sources of forgetting, and introduce a catastrophic forgetting metric tailored to CKGE.

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
