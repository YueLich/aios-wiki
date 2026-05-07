---
title: "Skill Neologisms: Towards Skill-based Continual Learning"
arXiv: 2605.04970
date: 2026-05-06
tags: [continual-learning, skill-learning, agent-memory, soft-tokens]
reviewer: auto
source: arXiv RSS/API
---

# Skill Neologisms: Towards Skill-based Continual Learning

## 论文信息

- **arXiv ID**: 2605.04970
- **作者**: Antonin Berthon, Nicolas Astorga, Mihaela van der Schaar
- **发表日期**: 2026-05-06
- **方向**: 持续学习、技能学习
- **代码**: 未公开

## 摘要（翻译）

现代 LLM 展示了对越来越广泛的技能的掌握，以及灵活组合它们的能力。然而，以可扩展的方式扩展模型能力到新技能是一个开放问题：微调和参数高效变体面临灾难性遗忘风险，而基于上下文的方法表达能力有限并受限于模型的有效上下文。

本文探索 **skill neologisms**——即集成到模型词汇表中并针对特定技能优化以提高能力的软 token——作为在不更新权重的情况下选择性扩展模型能力到新技能的方法。

我们首先观察到现成的预训练 LLM 已经展现出与程序性知识相关的 token。然后表明，skill neologisms 可以被学习以提高特定技能的模型能力，同时与分布外技能可组合，并且独立训练的 skill neologisms 可以零样本组合。这些结果表明 skill neologisms 可能为基于技能的持续学习提供一条可扩展的路径。

## 核心贡献

### 1. Skill Neologisms 概念

**软 token vs 硬 token**：
- 传统 token：固定词汇表，硬编码语义
- Skill neologisms：可学习的软 token，与特定技能关联

**关键特性**：
- 无需权重更新：通过 prompt 或 hypernetwork 学习
- 可组合：多个 skill neologisms 可组合使用
- 零样本泛化：独立训练的 neologisms 可在新场景零样本组合

### 2. 与 Agent 记忆系统的关联

Skill neologisms 可以存储在 Agent 记忆中：
- 当 Agent 学习新技能时，可以创建对应的 neologism
- Neologisms 作为技能的"记忆钩子"存储
- 检索时通过 neologism 激活对应技能

### 3. 实验发现

1. **预训练 LLM 已具备相关 token**：说明程序性知识已存在于模型中
2. **可学习性**：skill neologisms 可以被优化以增强特定技能
3. **可组合性**：独立训练的 neologisms 可零样本组合
4. **分布外泛化**：组合后的 neologisms 在未见过的场景也有效

## 为什么重要

Skill neologisms 为持续学习提供了一条新路径：

1. **避免权重更新**：传统持续学习需要梯度下降，skill neologisms 只需学习少量软参数
2. **可组合性**：模块化的技能表示，支持灵活的技能组合
3. **零样本迁移**：训练好的 neologisms 可在新场景直接使用

## 与端侧/移动端相关性

1. **参数高效**：无需更新大模型权重，适合端侧资源受限场景
2. **按需加载**：技能 neologisms 可在需要时动态加载到上下文
3. **模块化管理**：每个 neologism 可独立存储、更新、组合
