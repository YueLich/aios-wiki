---
title: "From Soliloquy to Agora: Memory-Enhanced LLM Agents with Decentralized Debate for Optimization Modeling"
arXiv: 2604.25847
date: 2026-04-28
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Jianghao Lin, Zi Ling, Chenyu Zhou, Tianyi Xu, Ruoqing Jiang, Zizhuo Wang, Dongdong Ge
- **提交日期**: 2026-04-28

## 摘要

Optimization modeling underpins real-world decision-making in logistics, manufacturing, energy, and public services, but reliably solving such problems from natural-language requirements remains challenging. This paper proposes a multi-agent debate system where each agent maintains its own memory of past optimization attempts and solution patterns. Agents propose candidate formulations, debate their merits using stored experiences, and iteratively refine solutions. The decentralized debate enables exploration of multiple modeling paradigms simultaneously, while memory allows agents to build on previous successes and avoid repeated failures. Memory is structured as case-based reasoning: new optimization problems are matched against historical cases, retrieving similar problem-solving experiences.

## 核心贡献

1. **多 Agent 辩论系统**: 每个 Agent 维护独立记忆，提出候选方案并辩论
2. **案例推理记忆**: 将新问题与历史案例匹配，检索相似问题解决经验
3. **多范式同时探索**: 去中心化辩论使多种建模范式可同时探索

## 为什么重要

展示了记忆在多 Agent 协作中的关键作用——记忆使 Agent 能够从过去的成功和失败中学习，而非盲目重复试错。

## 与端侧/移动端的相关性

多 Agent 系统计算开销较大，端侧适用场景有限。但案例推理记忆结构本身可迁移到端侧，用于轻量优化问题求解。
