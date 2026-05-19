---
title: "Remembering More, Risking More: Longitudinal Safety Risks in Memory-Equipped LLM Agents"
arXiv: 2605.17830
date: 2026-05-18
tags: [memory-privacy, safety, longitudinal-risk, adversarial]
reviewer: auto
source: arXiv API
---

## 摘要

Safety evaluations of memory-equipped LLM agents typically measure within-task safety: whether an agent completes a single scenario safely, often under adversarial conditions such as prompt injection or memory poisoning. In deployment, however, a single agent serves many independent tasks over a long horizon, and memory accumulated during earlier tasks can affect behavior on later, unrelated ones. Studying this regime requires evaluation along the temporal dimension across tasks: not whether an agent is safe at any single memory state, but how its safety profile changes as memory accumulates across many independent interactions. We call this failure mode temporal memory contamination. To isolate memory exposure from stream non-stationarity, we introduce a trigger-probe protocol that evaluates a fixed probe set against read-only memory snapshots at varying prefix lengths, together with a NullMemory counterfactual baseline for identifying memory-induced violations. We apply this protocol across three deployment scenarios spanning records, memos, forms, and email correspondence and eight memory architectures, and additionally on Claw-like AI agents, such as OpenClaw, using the platform's native memory mechanism. Memory-enabled agents consistently exceed the NullMemory baseline, and memory-induced violation rates show a robust upward trend with exposure length on both agent classes. Order-randomization experiments indicate that the effect is driven primarily by accumulated content rather than encounter order. Finally, a structural consequence of the event decomposition is that memory-induced risk is detectable from retrieval state before generation, which we confirm with a high-recall diagnostic monitor. Our results argue for treating memory safety as a longitudinal property that requires temporal evaluation, not a single-state property that can be captured by a snapshot.

## 核心贡献

1. **提出Memory方法** — 针对现有记忆系统在安全评估方面的不足
2. **关键设计** — 跨任务纵向安全风险评估框架
3. **实验验证** — 在纵向安全评估上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：首次系统性地研究了记忆增强Agent的纵向安全风险
- **实践价值**：为部署记忆增强Agent提供了安全指南

## 与端侧/移动端的相关性

长期安全风险评估对移动端部署至关重要

## 参考文献

（参考文献待从原文补充）
