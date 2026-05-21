---
title: AMemGym: Interactive Memory Benchmarking for Assistants in Long-Horizon Conversations
arXiv: 2603.01966
date: 2026-03-02
tags: ['agent-memory', 'memory-retrieval', 'benchmark', 'conversational-memory', 'evaluation']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

Long-horizon interactions between users and LLM-based assistants necessitate effective memory management, yet current approaches face challenges in training and evaluation of memory. Existing memory benchmarks rely on static, off-policy data as context, limiting evaluation reliability and scalability.

The authors introduce AMemGym, an interactive environment enabling on-policy evaluation and optimization for memory-driven personalization. AMemGym employs structured data sampling to predefined user profiles, state-dependent questions, and state evolution trajectories, enabling cost-effective generation of high-quality, evaluation-aligned interactions.

LLM-simulated users expose latent states through role-play while maintaining structured state consistency. Comprehensive metrics based on structured data guide both assessment and optimization of assistants.

Experiments reveal performance gaps in existing memory systems (e.g., RAG, long-context LLMs, and agentic memory) and corresponding reasons. AMemGym not only enables effective selection among competing approaches but can also drive the self-evolution of memory management strategies.

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
