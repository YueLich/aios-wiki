---
title: "State Contamination in Memory-Augmented LLM Agents"
arXiv: 2605.16746
date: 2026-05-16
tags: [memory-privacy, state-contamination, safety, memory-poisoning]
reviewer: auto
source: arXiv API
---

## 摘要

LLM agents increasingly rely on persistent state, including transcripts, summaries, retrieved context, and memory buffers, to support long-horizon interaction. This makes safety depend not only on individual model outputs, but also on what an agent stores and later reuses. We study a failure mode we call memory laundering: toxic or adversarial context can be compressed into memory summaries that no longer appear toxic under standard detectors, while still preserving hostile framing or conflict structure that influences future generations. Using paired counterfactual multi-agent rollouts, we show that toxic-origin memory summaries can remain below common toxicity thresholds while nevertheless increasing downstream toxicity relative to matched neutral baselines. To measure this hidden influence, we introduce the sub-threshold propagation gap (SPG), which quantifies downstream behavioral differences conditioned on memory states that a deployed monitor would classify as safe. Our experiments show that toxicity propagates through distinct state channels: raw transcript reuse drives overt downstream toxicity, while compressed memory carries hidden sub-threshold influence. We further find that mitigation depends critically on intervention placement. Sanitizing toxic state before summarization substantially reduces the hidden propagation gap, whereas cleaning only the completed summary can leave laundered influence intact. These results suggest that safety in memory-augmented agents should be treated as a state-control problem over evolving context, with sanitization applied before unsafe information is compressed into persistent memory.

## 核心贡献

1. **提出State方法** — 针对现有记忆系统在状态污染问题方面的不足
2. **关键设计** — 状态污染的识别与防御机制
3. **实验验证** — 在记忆污染场景上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：揭示了记忆状态污染这一新安全威胁
- **实践价值**：为防御记忆污染提供了理论基础

## 与端侧/移动端的相关性

状态污染防御对移动端持久化Agent尤为重要

## 参考文献

（参考文献待从原文补充）
