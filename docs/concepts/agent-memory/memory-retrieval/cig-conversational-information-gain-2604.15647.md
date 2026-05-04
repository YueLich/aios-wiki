---
title: CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics
arXiv: 2604.15647
date: 2026-04-17
tags: [agent-memory, memory_retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.15647
- **作者**: Ming-Bin Chen, Jey Han Lau, Lea Frermann
- **提交日期**: 2026-04-17

## 摘要

Measuring the quality of public deliberation requires evaluating not only civility or argument structure, but also the informational progress of a conversation. We introduce a framework for Conversational Information Gain (CIG) that evaluates each utterance in terms of how it advances collective understanding of the target topic.

To operationalize CIG, we model an evolving semantic memory of the discussion: the system extracts atomic claims from utterances and incrementally consolidates them into a structured memory state. Using this memory, we score each utterance along three interpretable dimensions: novelty (does it add new information?), relevance (does it address prior claims?), and coherence (does it fit the current discourse?).

This memory-based evaluation framework enables fine-grained tracking of information flow in deliberative dialogues, revealing how different participants contribute to collective understanding over time. The semantic memory captures both what has been established and what remains contested, providing a grounded basis for evaluating information gain rather than relying on surface-level metrics.

Experiments on multiple deliberation corpora demonstrate that CIG correlates with human judgments of discussion quality and provides actionable insights into how collective understanding evolves through dialogue.

## 核心贡献

1. **问题定义**: CIG 针对 memory retrieval 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 memory、retrieval 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
