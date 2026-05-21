---
title: Memex(RL): Scaling Long-Horizon LLM Agents via Indexed Experience Memory
arXiv: 2603.04257
date: 2026-03-04
tags: ['agent-memory', 'memory-retrieval', 'context-compression', 'indexed-memory', 'long-horizon']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

LLM agents are fundamentally bottlenecked by finite context windows on long-horizon tasks. As trajectories grow, retaining tool outputs and intermediate reasoning in-context quickly becomes infeasible. Existing solutions typically shorten context through truncation or running summaries, but these methods are fundamentally lossy because they compress or discard past evidence itself.

The authors introduce Memex, an indexed experience memory mechanism that compresses context without discarding evidence. Memex maintains a compact working context consisting of concise structured summaries and stable indices, while storing full-fidelity underlying interactions in an external experience database under those indices. The agent can decide when to dereference an index and recover the exact past evidence needed for the current subgoal.

They optimize both write and read behaviors with a reinforcement learning framework MemexRL, using reward shaping tailored to indexed memory usage under a context budget. Theoretical analysis shows the Memex loop can preserve decision quality with bounded dereferencing while keeping effective in-context computation bounded as history grows.

Empirically, on challenging long-horizon tasks, Memex agent trained with MemexRL improves task success while using a significantly smaller working context.

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
