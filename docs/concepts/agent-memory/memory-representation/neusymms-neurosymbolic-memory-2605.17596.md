---
title: "NeuSymMS: A Hybrid Neuro-Symbolic Memory System for Persistent, Self-Curating LLM Agents"
arXiv: 2605.17596
date: 2026-05-17
tags: [memory-representation, neuro-symbolic, persistence, CLIPS]
reviewer: auto
source: arXiv API
---

## 摘要

We present NeuSymMS, an adaptive memory system that enables large language model (LLM) agents to learn, remember, and reason about users across sessions via a hybrid neuro-symbolic architecture. NeuSymMS couples neural fact extraction from unstructured dialogue with a CLIPS-based expert system that classifies, deduplicates, and reconciles facts under explicit lifecycle rules. The system represents knowledge as subject-relation-value triples stored in relational database management system, supports user/agents/agent-to-agents scoping, and implements a dual-horizon short-term/long-term memory model with access-based promotion and time-based pruning. NeuSymMS maintains continuity of memory while avoiding context-window bloat and cross-entity contamination. We argue that this architecture offers a practical path to trustworthy, auditable memory for production agentic systems and discuss its novelty relative to log retrieval, summarization, and key-value approaches.

## 核心贡献

1. **提出Neusymms方法** — 针对现有记忆系统在记忆持久化方面的不足
2. **关键设计** — 神经符号混合架构结合CLIPS专家系统
3. **实验验证** — 在对话记忆与跨会话推理上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：设计了一套自适应神经符号记忆系统
- **实践价值**：支持跨会话的用户记忆与推理

## 与端侧/移动端的相关性

混合架构可在服务器端运行复杂推理，边缘端轻量级提取

## 参考文献

（参考文献待从原文补充）
