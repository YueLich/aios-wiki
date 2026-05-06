---
title: "When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents"
arXiv: 2604.27003
date: 2026-04-29
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents

**作者:** Qisheng Hu, Quanyu Long, Wenya Wang
**发表:** 2026-04-29

## 摘要

Memory-augmented LLM agents offer an appealing shortcut to continual learning: rather than updating model parameters, they accumulate experience in external memory, seemingly sidestepping the stability-plasticity dilemma of parametric learning. We show that this challenge does not disappear but resurfaces at the memory level. Under a limited context window, old and new experiences compete during retrieval, relocating the continual-learning bottleneck from parameter updates to memory access. To study this phenomenon, we introduce a (k,v) framework that disentangles two fundamental design axes of external memory: how experience is represented and how it is organized for retrieval.

## 核心贡献

1. **(k,v) 分析框架**: 将外部记忆的设计轴 disentangle 为经验表示（k）和检索组织（v）两个维度
2. **记忆层面的 CL 瓶颈迁移**: 证明持续学习的稳定性-可塑性困境不会消失，而是从参数更新迁移到记忆访问层
3. **抽象程序记忆优于详细轨迹**: 在 ALFWorld 和 BabyAI 的顺序任务实验中，抽象程序记忆比详细轨迹迁移更可靠
4. **负迁移的不对称伤害**: 负迁移对困难案例的伤害远大于对简单案例的伤害
5. **细粒度组织并非总是有益**: 产生强前向迁移的记忆组织可能同时引发严重遗忘

## 为什么重要

首次系统研究了在 LLM Agent 外部记忆环境中持续学习的瓶颈问题。揭示了一个根本洞察：外部记忆并没有解决持续学习问题，而是将其重新塑造为记忆表示和检索设计的问题。这对设计真正能够持续学习的 Agent 记忆系统有重要指导意义。

## 与端侧/移动端的相关性

端侧 Agent 依赖外部记忆来弥补参数规模限制，但本文表明外部记忆不会让持续学习问题消失——只是在不同层面重现。对于端侧设计，这意味着需要在记忆表示粒度和检索组织之间寻找新的平衡点，而非简单增加记忆容量。
