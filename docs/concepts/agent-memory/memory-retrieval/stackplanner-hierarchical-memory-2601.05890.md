---
title: StackPlanner: A Centralized Hierarchical Multi-Agent System with Task-Experience Memory Management
arXiv: 2601.05890
date: 2026-01-09
tags: ['agent-memory', 'memory-retrieval', 'multi-agent', 'experience-memory', 'coordination']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

Multi-agent systems based on large language models, particularly centralized architectures, have recently shown strong potential for complex and knowledge-intensive tasks. However, central agents often suffer from unstable long-horizon collaboration due to the lack of memory management, leading to context bloat, error accumulation, and poor cross-task generalization.

To address both task-level memory inefficiency and the inability to reuse coordination experience, the authors propose StackPlanner, a hierarchical multi-agent framework with explicit memory control. StackPlanner decouples high-level coordination from subtask execution with active task-level memory control, and learns to retrieve and exploit reusable coordination experience via structured experience memory and reinforcement learning.

Experiments on multiple deep-search and agent system benchmarks demonstrate the effectiveness of StackPlanner in enabling reliable long-horizon multi-agent collaboration.

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
