---
title: EquiMem: Calibrating Shared Memory in Multi-Agent Debate via Game-Theoretic Equilibrium
arXiv: 2605.09278
date: 2026-05-10
tags: [agent-memory, memory-retrieval, multi-agent]
reviewer: auto
source: arXiv API
---

# EquiMem: Calibrating Shared Memory in Multi-Agent Debate via Game-Theoretic Equilibrium

**arXiv**: 2605.09278 | **Date**: 2026-05-10 | **Category**: cs.AI

## 摘要

Multi-agent debate (MAD) systems increasingly rely on shared memory to support long-horizon reasoning, but this convenience opens a critical vulnerability: a single corrupted entry can contaminate the downstream memory-augmented reasoning, and debate alone fails to filter such errors. Existing safeguards filter entries via heuristics or LLM-based validation, yet they rely on AI judgments that share the same failure modes and overlook the cross-agent dynamics of MAD. We address this gap by formulating memory updating in MAD as a zero-trust memory game, in which no agent is assumed honest and the game equilibrium serves as an indicator of optimal memory trust. Guided by this equilibrium, we propose EquiMem, an inference-time calibration mechanism that quantifies each update algorithmically against the shared memory state, using agents existing retrieval queries and traversal paths as evidence rather than soliciting any LLM judgment. EquiMem instantiates calibration for both embedding- and graph-based memory, and across diverse benchmarks, MAD frameworks, and memory architectures, it consistently outperforms existing safeguards, remains robust under adversarial agents, and incurs negligible inference overhead.

## 核心贡献

1. **方法创新**: 待补充
2. **实验验证**: 待补充
3. **理论分析**: 待补充

## 为什么重要

本论文提出了针对agent-memory; memory-retrieval; multi-agent的关键改进，对端侧/移动端记忆系统具有参考价值。

## 与移动端/端侧相关性

- 待补充：具体应用场景和部署考量

## 参考文献

待补充
