---
title: "Clustering-driven Memory Compression for On-device Large Language Models"
arXiv: 2601.17443
date: 2026-01-24
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Clustering-driven Memory Compression for On-device Large Language Models

**作者:** Ondrej Bohdal, Pramit Saha, Umberto Michieli, Mete Ozay, Taha Ceritli  
**发表:** 2026-01-24

## 摘要

Large language models (LLMs) often rely on user-specific memories distilled from past interactions to enable personalized generation. A common practice is to concatenate these memories with the input prompt, but this approach quickly exhausts the limited context available in on-device LLMs. Compressing memories by averaging can mitigate context growth, yet it frequently harms performance due to semantic conflicts across heterogeneous memories. In this work, we introduce a clustering-based memory compression strategy that balances context efficiency and personalization quality. Our method groups memories by similarity and merges them within clusters prior to concatenation, thereby preserving coherence while reducing redundancy. Experiments demonstrate that our approach substantially lowers the number of memory tokens while outperforming baseline strategies such as naive averaging or direct concatenation. Furthermore, for a fixed context budget, clustering-driven merging yields more compact memory representations and consistently enhances generation quality.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
