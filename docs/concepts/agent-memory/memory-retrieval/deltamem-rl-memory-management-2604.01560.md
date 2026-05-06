---
title: "DeltaMem: RL-Driven Adaptive Memory Management for Long-Context LLM Agents"
arXiv: 2604.01560
date: 2026-04-02
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# DeltaMem: RL-Driven Adaptive Memory Management for Long-Context LLM Agents

## 论文基本信息

- **作者**: Ziqi Lei, Lin Liu, Chuan Chen, Yuxuan Wang, Jia扣
- **arXiv**: https://arxiv.org/abs/2604.01560
- **领域**: cs.AI, cs.CL

## 摘要

LLM Agent 在长上下文场景中面临记忆管理难题：保留全部历史导致上下文爆炸，粗暴截断又丢失关键信息。DeltaMem 提出用强化学习（RL）自适应管理记忆，根据任务相关性动态决定记忆的保留、压缩或遗忘策略。该框架将记忆管理建模为马尔可夫决策过程，通过与任务环境的交互学习最优记忆策略。在长对话、长 horizon 任务规划等场景中，DeltaMem 在保持 95% 任务性能的同时，将上下文长度减少 60%。

## 核心贡献

1. **RL-based Memory Management**: 首个将强化学习用于 Agent 记忆管理决策的框架
2. **Adaptive Memory Policy**: 根据任务上下文自适应选择保留/压缩/遗忘策略
3. **60% Context Reduction**: 在保持 95% 任务性能下减少 60% 上下文长度
4. **MDP-based Memory MDP**: 将记忆管理建模为状态=当前上下文+任务历史，动作=记忆操作
5. **通用框架**: 可与任何 LLM Agent 集成，适用于对话、规划、推理等多种任务

## 研究背景与问题

传统 Agent 记忆方法依赖固定策略（摘要频率、固定窗口大小），无法适应不同任务的需求。RL 在其他 Agent 组件（工具使用、规划）上已展现优势，但尚未系统性地应用于记忆管理。学习自适应记忆策略是解决固定策略局限性的自然方向。

## 核心方法

1. **Memory MDP**: 状态空间 = 当前上下文表示 + 任务嵌入；动作空间 = {保留, 压缩, 遗忘}
2. **Reward Shaping**: 奖励 = 任务完成质量 - 计算成本（与上下文长度相关）
3. **Policy Gradient 训练**: 使用 PPO 变体训练记忆管理策略网络
4. **Task-aware Encoder**: 任务嵌入由 LLM 编码，用于 condition 记忆策略
5. **Hierarchical Actions**: 动作可细化为不同粒度（保留特定 token/句子/段落）

## 为什么重要

DeltaMem 证明了"记忆管理"本身可以作为 RL 学习的技能，而非手工设计的规则。这为 Agent 记忆系统开辟了自适应学习的新方向。相比手工记忆策略，RL 学到的策略能更好地平衡任务性能与计算效率。

## 与移动端/端侧相关性

1. **自适应粒度**: RL 策略可学会在资源紧张时更激进地压缩，适合端侧动态资源分配
2. **60% 上下文减少**: 显著降低移动端 LLM 推理的内存和计算需求
3. **离线可学习**: 策略网络可预先训练好，推理时无需 online 学习
4. **多任务泛化**: 学到的策略可跨任务泛化，减少每个新场景的调优需求
