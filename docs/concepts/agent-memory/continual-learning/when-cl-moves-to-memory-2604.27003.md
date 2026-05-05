---
title: "When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents"
arXiv: 2604.27003
date: 2026-04-29
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents

## 论文基本信息

- **作者**: Qisheng Hu, Quanyu Long, Wenya Wang
- **arXiv**: https://arxiv.org/abs/2604.27003
- **领域**: cs.LG
- **备注**: Working in progress

## 摘要

Memory-augmented LLM agents offer an appealing shortcut to continual learning: rather than updating model parameters, they accumulate experience in external memory, seemingly sidestepping the stability-plasticity dilemma of parametric learning. We show that this challenge does not disappear but resurfaces at the memory level. Under a limited context window, old and new experiences compete during retrieval, relocating the continual-learning bottleneck from parameter updates to memory access. To study this phenomenon, we introduce a (k,v) framework that disentangles two fundamental design axes of external memory: how experience is represented and how it is organized for retrieval. Across sequential-task experiments in ALFWorld and BabyAI, we find that abstract procedural memories transfer more reliably than detailed trajectories, while negative transfer disproportionately harms the hard cases. Moreover, finer-grained memory organization is not universally beneficial: designs that yield strong forward transfer can simultaneously induce severe forgetting. Together, these results reveal that external memory does not resolve the continual-learning problem; it reshapes it into a problem of memory representation and retrieval design.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
