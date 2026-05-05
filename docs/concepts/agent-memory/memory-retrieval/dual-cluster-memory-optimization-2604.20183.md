---
title: "Dual-Cluster Memory Agent: Resolving Multi-Paradigm Ambiguity in Optimization Problem Solving"
arXiv: 2604.20183
date: 2026-04-13
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Xinyu Zhang, Yuchen Wan, Boxuan Zhang, Zesheng Yang, Lingling Zhang, Bifan Wei, Jun Liu
- **提交日期**: 2026-04-13

## 摘要

Large Language Models (LLMs) often struggle with structural ambiguity in optimization problems, where a single problem admits multiple related but conflicting modeling paradigms, hindering effective solving. This paper proposes Dual-Cluster Memory, where the agent maintains two parallel memory stores representing different optimization paradigms (e.g., continuous vs. discrete, linear vs. nonlinear). Each cluster stores problem-solving experiences in its paradigm's language. When faced with a new problem, the agent retrieves candidates from both clusters and uses a meta-learner to decide which paradigm is more appropriate. The dual-cluster structure forces the agent to explicitly consider paradigm alternatives rather than defaulting to familiar approaches.

## 核心贡献

1. **双簇记忆架构**: 两个并行记忆存储代表不同优化范式
2. **范式元学习器**: 预测哪种范式更适合当前问题
3. **显式范式考虑**: 强制 Agent 考虑范式替代方案，而非默认熟悉方法

## 为什么重要

解决了优化问题中的结构歧义这一 LLM 的核心弱点，通过双簇记忆实现范式级别的推理。

## 与端侧/移动端的相关性

双簇结构简单高效，适合端侧部署。在边缘优化场景（如移动端物流规划）中有应用潜力。
