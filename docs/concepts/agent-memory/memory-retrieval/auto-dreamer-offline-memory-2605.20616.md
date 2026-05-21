---
title: "Auto-Dreamer: Learning Offline Memory Consolidation for Language Agents"
arXiv: "2605.20616"
date: "2026-05-20"
tags: [agent-memory, memory-consolidation, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Auto-Dreamer: Learning Offline Memory Consolidation for Language Agents
- **arXiv ID**: 2605.20616
- **作者**: Chongrui Ye, Yuxiang Liu, Yu Wang, Haofei Yu, Yining Zhao, Ge Liu, Julian McAuley, Jiaxuan You
- **发表日期**: 2026-05-20
- **方向**: Agent Memory / Memory Consolidation

## 核心贡献

1. **离线记忆整合框架**: 提出 Auto-Dreamer，一种将积累的经验转化为可复用知识的离线记忆整合方法，将记忆获取与整合解耦。
2. **全局视图发现**: 允许 Agent 跨会话发现重复模式、抽象共享过程、剪枝冗余条目，获得单一在线过程无法提供的全局视角。
3. **互补学习启发的整合**: 借鉴互补学习系统（Complementary Learning Systems）理论，在离线阶段进行记忆整合，避免在线学习的计算开销。

## 摘要

Language agents increasingly operate over streams of related tasks, yet existing memory systems struggle to convert accumulated experience into reusable knowledge. Retrieval-augmented and structured memory methods record per-session observations effectively, but often couple acquisition and consolidation into a single online process, leaving the agent without a global view across sessions to discover recurring patterns, abstract shared procedures, or prune redundant entries. Inspired by complementary learning systems theory, we propose Auto-Dreamer, which decouples memory acquisition from consolidation and performs offline consolidation to transform accumulated experience into structured, reusable knowledge.

## 详细解读

### 研究背景

当前语言 Agent 的记忆系统面临一个根本性困境：获取（acquisition）和整合（consolidation）被耦合在同一个在线过程中。在线整合虽然实时，但 Agent 只能看到当前会话的局部信息，无法发现跨会话的重复模式或抽象出共享知识结构。

### 核心方法

Auto-Dreamer 的核心设计：
- **离线整合**: 在积累了一定经验后，Agent 进入离线阶段进行记忆整合
- **跨会话全局分析**: 离线阶段可以访问所有历史会话，发现重复出现的模式和共享结构
- **知识抽象与剪枝**: 从具体经验中抽象出高层次模式，同时剪枝冗余或过时的记忆条目
- **受互补学习系统启发**: 借鉴神经科学中的记忆巩固理论，在离线期间进行记忆的结构化重组

### 与现有方法的区别

现有的 RAG 和结构化记忆方法在单会话层面记录观察很有效，但缺乏跨会话的全局优化能力。Auto-Dreamer 通过显式的离线整合阶段弥补了这一缺陷。

## 为什么重要

这篇工作揭示了记忆获取与整合解耦的重要性。在实际应用中，离线整合允许更充分的知识抽象，且不占用在线响应时间。对移动端 Agent 尤其有价值，因为离线整合可以在设备空闲时（如夜间充电时）进行，不影响用户体验。

## 与端侧/移动端的相关性

离线记忆整合对移动端 Agent 特别友好——可以在设备空闲时执行，不影响实时响应速度。同时，全局视图的知识抽象能显著压缩存储开销，对移动设备的有限存储空间尤为重要。

## 参考文献

（参考文献待从原文补充）
