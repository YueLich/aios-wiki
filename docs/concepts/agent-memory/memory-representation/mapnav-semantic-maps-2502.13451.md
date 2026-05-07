---
title: MapNav - A Novel Memory Representation via Annotated Semantic Maps for Vision-and-Language Navigation
arXiv: 2502.13451
date: 2025-02-19
tags: [agent-memory, spatial-memory, embodied-AI, navigation]
reviewer: auto
source: arXiv API
---

# MapNav: Annotated Semantic Maps for Vision-and-Language Navigation

## 摘要

视觉-语言导航（VLN）是具身 AI 的关键任务，要求 Agent 在遵循自然语言指令的同时导航多样化的未见环境。传统方法严重依赖历史观测作为时空上下文进行决策，导致对长期记忆的利用不足。本文提出 MapNav，通过注释语义地图引入一种全新的记忆表征，将 Agent 的历史体验转化为结构化的空间知识。MapNav 支持高效的地图查询和推理，使 Agent 能够在导航过程中利用累积的环境记忆。

## 核心贡献

1. **注释语义地图记忆**：用结构化地图而非原始图像序列存储环境记忆
2. **语言对齐的空间记忆**：地图中的每个语义区域与语言描述对齐
3. **高效地图查询**：支持基于语言的空间推理查询
4. **跨任务泛化**：地图记忆可迁移到不同下游任务
5. **增量地图构建**：支持 Agent 在探索过程中逐步构建地图记忆

## 技术方法

### 语义地图表征
- 将环境表示为带有语义注释的拓扑地图
- 每个节点：空间位置 + 视觉特征 + 语义标签
- 边：空间连通性 + 导航关系

### 记忆构建
1. Agent 探索环境时构建局部地图
2. 将语言指令中的目标与地图节点对齐
3. 在地图上存储路径和决策上下文

### 导航推理
- 给定语言指令，查询地图获取相关记忆
- 支持"之前去过的地方"、"目标在哪里"等空间推理
- 融合地图记忆与实时感知

## 为什么重要

MapNav 展示了"空间记忆"对具身 Agent 的重要性。之前的 VLN 方法缺乏有效存储和利用历史探索结果的手段，MapNav 通过语义地图将感知序列化记忆转化为结构化知识，使得 Agent 能够真正"记住"去过的环境和学到的导航经验。

## 与移动端/端侧相关性

1. **家庭机器人**：记住房间布局和物品位置
2. **AR 导航**：持久化空间记忆，支持室内导航
3. **仓库机器人**：构建和利用环境地图记忆
4. **端侧地图存储**：结构化地图比原始图像更节省存储空间

## 参考文献

- Lingfeng Zhang, Xiaoshuai Hao, Qinwen Xu, Qiang Zhang. "MapNav: A Novel Memory Representation via Annotated Semantic Maps for Vision-and-Language Navigation." arXiv:2502.13451, 2025.
