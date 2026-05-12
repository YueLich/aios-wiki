---
title: MemReread: Enhancing Agentic Long-Context Reasoning via Memory-Guided Rereading
arXiv: 2605.10268
date: 2026-05-11
tags: [agent-memory, memory-retrieval, long-context]
reviewer: auto
source: arXiv API
---

# MemReread: Enhancing Agentic Long-Context Reasoning via Memory-Guided Rereading

**arXiv**: 2605.10268 | **Date**: 2026-05-11 | **Category**: cs.CL

## 摘要

To tackle long-context reasoning tasks without the quadratic complexity of standard attention mechanisms, approaches based on agent memory have emerged, which typically maintain a dynamically updated memory when linearly processing document chunks. To mitigate the potential loss of latent evidence in this memorize-while-reading paradigm, recent works have integrated retrieval modules that allow agents to recall information previously discarded during memory overwriting. However, retrieval-based recall suffers from both evidence loss during memory formation and interference induced by invalid queries. To overcome these limitations, we propose MemReread. Built upon streaming reading, MemReread circumvents intermediate retrieval. It triggers question decomposition and rereading when the final memory is insufficient, enabling the recovery of indirect facts that were prematurely discarded. This design supports non-linear reasoning while preserving the inherent logical flow of document comprehension. To further enhance practicality, we introduce a reinforcement learning framework that enhances length extrapolation capability while dynamically determining the number of rereading passes based on task complexity, thereby flexibly controlling computational overhead. Extensive experiments demonstrate that MemReread consistently outperforms baseline frameworks on long-context reasoning tasks, while maintaining linear time complexity with respect to context length.

## 核心贡献

1. **方法创新**: 待补充
2. **实验验证**: 待补充
3. **理论分析**: 待补充

## 为什么重要

本论文提出了针对agent-memory; memory-retrieval; long-context的关键改进，对端侧/移动端记忆系统具有参考价值。

## 与移动端/端侧相关性

- 待补充：具体应用场景和部署考量

## 参考文献

待补充
