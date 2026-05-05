---
title: "MemORAI: Memory Organization and Retrieval via Adaptive Graph Intelligence for LLM Conversational Agents"
arXiv: 2605.01386
date: 2026-05-11
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Hung Pham Van, Nguyen Manh Hieu, Khang Pham Tran Tuan, Nam Le Hai, Linh Ngo Van, Nguyen Thi Ngoc Diep, Trung Le
- **提交日期**: 2026-05-11

## 摘要

Large Language Models (LLMs) lack persistent memory for long-term personalized conversations. Existing graph-based memory systems suffer from information dilution, absent provenance tracking, and uniform granularity, leading to suboptimal retrieval. MemORAI proposes an Adaptive Graph Intelligence approach with two key innovations: (1) dynamic memory organization that adapts granularity based on conversation context, and (2) provenance-aware retrieval that tracks information origins to enable source verification. The system maintains a hierarchical memory graph where nodes represent concepts at varying abstraction levels, with edges encoding semantic relationships and provenance chains. During retrieval, the system can trace extracted information back to its origin conversation turn, enabling explainability. Experiments on long-term conversation benchmarks show MemORAI outperforms existing graph memory systems by 15-25% on task completion while reducing hallucination through provenance tracking.

## 核心贡献

1. **动态记忆组织 (Dynamic Memory Organization)**: 根据对话上下文自适应调整记忆粒度，避免信息稀释
2. **溯源感知检索 (Provenance-Aware Retrieval)**: 通过追踪信息来源链，支持结果可解释性
3. **层次记忆图谱**: 节点表示不同抽象级别的概念，边缘编码语义关系和溯源链

## 为什么重要

现有图记忆系统在长期对话中信息稀释严重，且缺乏溯源能力。MemORAI 通过自适应粒度和溯源跟踪解决了这两个核心问题，对于需要高精度记忆的 Agent 应用（如医疗咨询、法律对话）具有重要价值。

## 与端侧/移动端的相关性

层次图结构对计算资源有一定要求，端侧部署需要图剪枝优化。但溯源机制可简化为轻量版本，适用于资源受限场景。
