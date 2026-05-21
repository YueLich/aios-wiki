---
title: UI-Mem: Self-Evolving Experience Memory for Online Reinforcement Learning in Mobile GUI Agents
arXiv: 2602.05832
date: 2026-02-05
tags: ['agent-memory', 'memory-retrieval', 'gui-agent', 'experience-memory', 'reinforcement-learning', 'mobile']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

Online Reinforcement Learning (RL) offers a promising paradigm for enhancing GUI agents through direct environment interaction. However, its effectiveness is severely hindered by inefficient credit assignment in long-horizon tasks and repetitive errors across tasks due to the lack of experience transfer.

The authors propose UI-Mem, a framework that enhances GUI online RL with a Hierarchical Experience Memory. Unlike traditional replay buffers, UI-Mem accumulates structured knowledge including high-level workflows, subtask skills, and failure patterns, stored as parameterized templates that enable cross-task and cross-application transfer.

To effectively integrate memory guidance into online RL, they introduce Stratified Group Sampling, which injects varying levels of guidance across trajectories within each rollout group to maintain outcome diversity, driving the unguided policy toward internalizing guided behaviors. A Self-Evolving Loop continuously abstracts novel strategies and errors to keep the memory aligned with the agent's evolving policy.

Experiments on online GUI benchmarks demonstrate that UI-Mem significantly outperforms traditional RL baselines and static reuse strategies, with strong generalization to unseen applications. Project page: https://ui-mem.github.io

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
