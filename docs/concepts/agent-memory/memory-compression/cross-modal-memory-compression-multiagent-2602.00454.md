---
title: "Cross-Modal Memory Compression for Efficient Multi-Agent Debate"
arXiv: 2602.00454
date: 2026-01-31
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Cross-Modal Memory Compression for Efficient Multi-Agent Debate

**作者:** Jing Wu, Yue Sun, Tianpei Xie, Suiyao Chen, Jingyuan Bao et al.  
**发表:** 2026-01-31

## 摘要

Multi-agent debate can improve reasoning quality and reduce hallucinations, but it incurs rapidly growing context as debate rounds and agent count increase. Retaining full textual histories leads to token usage that can exceed context limits and often requires repeated summarization, adding overhead and compounding information loss. We introduce DebateOCR, a cross-modal compression framework that replaces long textual debate traces with compact image representations, which are then consumed through a dedicated vision encoder to condition subsequent rounds. This design compresses histories that commonly span tens to hundreds of thousands of tokens, cutting input tokens by more than 92% and yielding substantially lower compute cost and faster inference across multiple benchmarks. We further provide a theoretical perspective showing that diversity across agents supports recovery of omitted information: although any single compressed history may discard details, aggregating multiple agents' compressed views allows the collective representation to approach the information bottleneck with exponentially high probability.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
