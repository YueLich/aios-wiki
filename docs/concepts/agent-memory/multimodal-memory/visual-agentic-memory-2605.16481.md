---
title: "Visual Agentic Memory: Enabling Online Long Video Understanding via Online Indexing, Hierarchical Memory, and Agentic Retrieval"
arXiv: 2605.16481
date: 2026-05-15
tags: [multimodal-memory, video-understanding, hierarchical-memory, online-indexing]
reviewer: auto
source: arXiv API
---

## 摘要

Long video understanding requires more than large context windows. It also needs a memory mechanism that decides what visual evidence to retain, keeps it searchable over long horizons, and grounds later reasoning in recoverable observations rather than compressed latent state alone. We propose Visual Agentic Memory (VAM), a training-free framework with three components. Online Indexing supports selective evidence retention under streaming constraints. Hierarchical Memory organises retained evidence in a Parallel Representation that aligns temporal context with spatial observations. Agentic Retrieval searches, inspects, and verifies candidate evidence before producing a grounded answer. On OVO-Bench, VAM achieves the highest RT+BT average (68.41) across all reported baselines, improving over end-to-end use of the same underlying MLLM (Gemini 3 Flash, 67.46). On the month-scale split of MM-Lifelong train@month (105.6 hours over 51 days), VAM reaches 17.11%, second only to ReMA with GPT-5 (17.62%). These results suggest that long-horizon video understanding benefits from treating visual memory as an explicit, inspectable, and queryable substrate. Code is available at https://github.com/yiliu-li/Visual-Agentic-Memory.

## 核心贡献

1. **提出Visual方法** — 针对现有记忆系统在视觉记忆索引方面的不足
2. **关键设计** — 在线索引与层次化记忆的结合
3. **实验验证** — 在长视频理解上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：为长视频理解提供了记忆机制
- **实践价值**：实现了可在线索引的长期视觉记忆

## 与端侧/移动端的相关性

在线视频理解是智能摄像头的重要能力

## 参考文献

（参考文献待从原文补充）
