---
title: "When to Forget: A Memory Governance Primitive"
arXiv: 2604.12007
date: 2026-04-13
tags: [agent-memory, memory-governance, selective-forgetting]
reviewer: auto
source: arXiv API
authors: "Baris Simsek"
---

## 论文信息

- **arXiv**: 2604.12007
- **发表日期**: 2026-04-13
- **作者**: Baris Simsek
- **方向**: 记忆治理

## 摘要

> Agent memory systems accumulate experience but currently lack a principled operational metric for memory quality governance -- deciding which memories to trust, suppress, or deprecate as the agent's task distribution shifts. Write-time importance scores are static; dynamic management systems use LLM judgment or structural heuristics rather than outcome feedback. This paper proposes Memory Worth (MW): a two-counter per-memory signal that tracks how often a memory co-occurs with successful versus failed outcomes, providing a lightweight, theoretically grounded foundation for staleness detection,

## 核心贡献

提出 Memory Governance Primitive，用遗忘倒三角（forgetting cascade）作为记忆质量的运行时度量指标，超越静态重要性评分。

## 为什么重要

这篇论文探讨了 When to Forget: A Memory Governance Primitive，与 Agent 记忆系统的构建直接相关。

## 与端侧/移动端的相关性

该研究对 Agent 记忆系统有通用价值，端侧相关性需结合具体部署场景评估。

## 参考文献

- arXiv: 2604.12007 | https://arxiv.org/abs/2604.12007

