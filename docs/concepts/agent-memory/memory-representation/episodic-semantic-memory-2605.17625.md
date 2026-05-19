---
title: "Episodic-Semantic Memory Architecture for Long-Horizon Scientific Agents"
arXiv: 2605.17625
date: 2026-05-17
tags: [memory-representation, episodic-memory, semantic-memory, scientific-agents]
reviewer: auto
source: arXiv API
---

## 摘要

As Large Language Models (LLMs) evolve into persistent scientific collaborators, context window saturation has emerged as a critical bottleneck. Scientific workflows involving iterative data analysis and hypothesis refinement rapidly saturate even extended contexts with dense technical content, while monolithic approaches suffer from quadratic cost scaling and cognitive degradation. We evaluate a Dual Process Memory Architecture that decouples immediate episodic needs (constant 10-message window) from long-term consolidated knowledge (growing at approximately 3 tokens/message). Unlike prior social agent memory systems, our domain-specific consolidation addresses contradictory parameter evolution, multi-hop reasoning across experimental phases, and precise technical fact retention. Through large-scale evaluation spanning 15,000 messages with cross-model validation across six LLMs from three families (OpenAI, Anthropic, Google), totaling 1,440 queries, we establish three key findings. First, while full-context models fail at 10,000 messages due to context overflow, our system maintains 70-85% accuracy with 1-2 second latency using 62% fewer tokens (45,434 vs 120,000+ limit). Second, cross-model validation reveals architecture-level trade-offs independent of specific LLMs: Dual Process excels at numeric/temporal queries (65-90% accuracy) while RAG excels at historical retrieval (60-85%), suggesting complementary deployment strategies. Third, we identify a "Sim-to-Real" gap where synthetic tests maintain constant memory but realistic workflows exhibit linear growth (about 3 tokens/message), with consolidation quality emerging as the primary scalability bottleneck. The architecture successfully manages profiles with 14,000+ scientific facts (125k tokens), demonstrating that domain-specific memory consolidation enables sustained operation beyond full-context limits.

## 核心贡献

1. **提出Episodic方法** — 针对现有记忆系统在情景-语义记忆架构方面的不足
2. **关键设计** — 情景记忆与语义记忆的统一架构
3. **实验验证** — 在科学推理任务上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：解决了科学Agent的上下文饱和问题
- **实践价值**：支持长时间跨度的科学发现流程

## 与端侧/移动端的相关性

记忆压缩对移动端科学助手有直接价值

## 参考文献

（参考文献待从原文补充）
