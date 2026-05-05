---
title: "MELODI: Exploring Memory Compression for Long Contexts"
arXiv: 2410.03156
date: 2024-10-04
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# MELODI: Exploring Memory Compression for Long Contexts

**作者:** Yinpeng Chen, DeLesley Hutchins, Aren Jansen, Andrey Zhmoginov, David Racz et al.  
**发表:** 2024-10-04

## 摘要

We present MELODI, a novel memory architecture designed to efficiently process long documents using short context windows. The key principle behind MELODI is to represent short-term and long-term memory as a hierarchical compression scheme across both network layers and context windows. Specifically, the short-term memory is achieved through recurrent compression of context windows across multiple layers, ensuring smooth transitions between windows. In contrast, the long-term memory performs further compression within a single middle layer and aggregates information across context windows, effectively consolidating crucial information from the entire history. Compared to a strong baseline - the Memorizing Transformer employing dense attention over a large long-term memory (64K key-value pairs) - our method demonstrates superior performance on various long-context datasets while remarkably reducing the memory footprint by a factor of 8.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
