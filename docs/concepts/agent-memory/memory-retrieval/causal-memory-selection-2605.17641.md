---
title: "Causal Intervention-Based Memory Selection for Long-Horizon LLM Agents"
arXiv: 2605.17641
date: 2026-05-17
tags: [memory-retrieval, causal-inference, long-horizon, memory-selection]
reviewer: auto
source: arXiv API
---

## 摘要

Long-horizon LLM agents rely on persistent memory to support interactions across sessions, yet existing memory systems often retrieve context using semantic similarity or broad history inclusion, treating retrieved memories as uniformly useful. This assumption is fragile because memories may be topically related while remaining irrelevant, stale, or misleading. We propose Causal Memory Intervention (CMI), a causal memory-selection technique that estimates how candidate memories affect the model's answer under controlled interventions, selecting memories that improve task performance while suppressing unstable, irrelevant, or harmful ones. To evaluate this setting, we introduce Causal-LoCoMo, a causally annotated benchmark derived from long conversational data, where each example contains a user request, a structured memory bank, useful memories, irrelevant distractors, and synthetic harmful memories. We compare CMI against vector, graph, reflection, summary, full-history, and no-memory baselines. Results show that CMI achieves a stronger balance between answer quality and robustness to misleading memory, suggesting that reliable long-term memory requires selecting context based on causal usefulness rather than relevance alone. The full framework, benchmark construction code, and experimental pipeline are available at https://github.com/Saksham4796/causal-memory-intervention.

## 核心贡献

1. **提出Causal方法** — 针对现有记忆系统在长期记忆管理方面的不足
2. **关键设计** — 基于因果干预的记忆选择机制
3. **实验验证** — 在长期对话任务上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：引入了因果推断来选择性地保留记忆
- **实践价值**：避免了传统相似度检索的脆弱性

## 与端侧/移动端的相关性

因果选择机制计算开销低，适合资源受限设备

## 参考文献

（参考文献待从原文补充）
