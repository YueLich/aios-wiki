---
title: "Revisiting Catastrophic Forgetting in Continual Knowledge Graph Embedding"
arXiv: 2604.19401
date: 2026-04-21
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Revisiting Catastrophic Forgetting in Continual Knowledge Graph Embedding

**作者:** Gerard Pons, Carlos Escolano, Besim Bilalli, Anna Queralt  
**发表:** 2026-04-21

## 摘要

Knowledge Graph Embeddings (KGEs) support a wide range of downstream tasks over Knowledge Graphs (KGs). In practice, KGs evolve as new entities and facts are added, motivating Continual Knowledge Graph Embedding (CKGE) methods that update embeddings over time. Current CKGE approaches address catastrophic forgetting (i.e., the performance degradation on previously learned tasks) primarily by limiting changes to existing embeddings.
  However, we show that this view is incomplete. When new entities are introduced, their embeddings can interfere with previously learned ones, causing the model to predict them in place of previously correct answers. This phenomenon, which we call entity interference, has been largely overlooked and is not accounted for in current CKGE evaluation protocols. As a result, the assessment of catastrophic forgetting becomes misleading, and CKGE methods performance is systematically overestimated.
  To address this issue, we introduce a corrected CKGE evaluation protocol that accounts for entity interference. Through experiments on multiple benchmarks, we show that ignoring this effect can lead to performance overestimation of up to 25%, particularly in scenarios with significant entity growth. We further analyze how different CKGE methods and KGE models are affected by the different sources of forgetting, and introduce a catastrophic forgetting metric tailored to CKGE.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
