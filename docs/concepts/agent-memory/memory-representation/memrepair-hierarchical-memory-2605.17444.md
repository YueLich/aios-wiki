---
title: "MemRepair: Hierarchical Memory for Agentic Repository-Level Vulnerability Repair"
arXiv: 2605.17444
date: 2026-05-17
tags: [memory-representation, hierarchical-memory, code-repair, Vulnerability]
reviewer: auto
source: arXiv API
---

## 摘要

Modern software ecosystems face a rapidly growing number of disclosed vulnerabilities, increasing the need for automated repair techniques that can operate reliably at repository scale. Although Large Language Model (LLM)-based agents have recently shown promise for automated vulnerability repair (AVR), most existing systems still treat repair as a single generation step over the currently visible code context. As a result, they lack a persistent mechanism for reusing prior fixes or learning from failed validation attempts, which limits their effectiveness on complex, multi-file repair tasks. We present MemRepair, a memory-augmented agentic framework that formulates vulnerability repair as an iterative, experience-driven process. MemRepair combines three complementary memory layers, i.e., History-Fix, Security-Pattern, and Refinement-Trajectory memories, with a dynamic feedback-driven refinement loop. This design allows the agent to retrieve repository-specific repair conventions, apply reusable security defenses, and exploit prior "failure-to-success" trajectories to revise semantically invalid patches based on runtime evidence. We evaluate MemRepair on three representative repository-level vulnerability repair benchmarks: SEC-Bench, PatchEval (Python, Go, JavaScript), and the C++ subset of Multi-SWE-bench. MemRepair achieves state-of-the-art resolution rates of 58.0%, 58.2%, and 30.58%, respectively, outperforming strong general-purpose agents such as OpenHands and SWE-agent, as well as the specialized AVR tool InfCode-C++, while maintaining competitive repair cost. These results show that persistent, hierarchical repair memory can substantially improve the reliability of agentic vulnerability repair across diverse languages and repository settings.

## 核心贡献

1. **提出Memrepair方法** — 针对现有记忆系统在层次化记忆方面的不足
2. **关键设计** — 分层记忆结构支持代码库级漏洞修复
3. **实验验证** — 在代码修复任务上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：为代码库级漏洞修复提供了层次化记忆支持
- **实践价值**：提升了自动化代码修复的可靠性

## 与端侧/移动端的相关性

层次化记忆结构支持增量式代码理解

## 参考文献

（参考文献待从原文补充）
