---
title: MemReward: Graph-Based Experience Memory for LLM Reward Prediction with Limited Labels
arXiv: 2603.19310
date: 2026-03-13
tags: ['agent-memory', 'memory-retrieval', 'experience-memory', 'graph-memory', 'reinforcement-learning']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

Recent advances in LLMs have been driven by reinforcement-learning-based post-training, which requires multiple rollouts with rewards. However, obtaining ground truth labels for reward calculation is often expensive or time-consuming.

The authors introduce MemReward, a graph-based experience memory framework: an initial LLM policy generates rollouts for each query, each comprising a thinking process and a final answer, and these rollouts are stored as experience memory. Queries, thinking processes, and answers form nodes in a heterogeneous graph with similarity and structural edges; a GNN trained on labeled rollouts propagates rewards to unlabeled rollouts during online optimization.

Experiments on Qwen2.5-3B and 1.5B in mathematics, question answering, and code generation demonstrate that MemReward, with only 20% labels, achieves 97.3% of Oracle performance on 3B and 96.6% on 1.5B, surpassing Oracle in out-of-domain tasks. Performance scales smoothly with label budget, reaching 99.4% of Oracle at 70% labels.

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
