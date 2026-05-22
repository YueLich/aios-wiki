---
title: "REMem: Reasoning with Episodic Memory in Language Agent"
arXiv: "2602.13530"
date: "2026-02-13"
tags: [agent-memory, episodic-memory, reasoning, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# REMem: Reasoning with Episodic Memory in Language Agent

## 论文基本信息

- **arXiv ID**: 2602.13530
- **发表日期**: 2026-02-13
- **作者**: Yiheng Shu, Saisri Padmaja Jonnalagedda, Xiang Gao, Bernal Jiménez Gutiérrez, Weijian Qi, Kamalika Das, Huan Sun, Yu Su
- **方向**: Episodic Memory, Language Agent, Memory Reasoning
- **类别**: cs.AI

## 摘要

人类善于在时空上下文背景下记忆具体经历并对其进行跨事件推理（即情景记忆能力）。然而，当前语言 Agent 的记忆仍以语义记忆为主，无法有效回忆和推理交互历史。现有工作普遍存在以下问题：忽略情景性、缺乏显式事件建模、或过度强调简单检索而忽视复杂推理能力。本文提出 REMem，一个两阶段框架，用于构建和推理情景记忆：（1）离线索引阶段，将经历转化为混合记忆图谱，灵活关联时间感知的事实片段；（2）在线推理阶段，使用具备精心设计工具的 Agent 检索器对记忆图谱进行迭代检索。在四个情景记忆基准测试上的综合评估表明，REMem 大幅超越 Mem0 和 HippoRAG 2 等先进记忆系统，在情景回忆和推理任务上分别提升 3.4% 和 13.4%。

## 核心贡献

### 1. 情景记忆的核心挑战识别

论文系统性地识别并形式化了 Agent 情景记忆构建与推理的核心挑战：
- **情景性缺失**：现有方法缺乏对时空上下文背景的显式建模
- **事件建模不足**：没有显式的事件（event）概念，只有静态事实
- **推理能力薄弱**：过度强调检索，忽视了对记忆的深层推理

### 2. 混合记忆图谱（Hybrid Memory Graph）

离线索引阶段，REMem 将 Agent 的交互经历转化为混合记忆图谱：
- **时间感知的事实片段（Time-aware Gists）**：保留经历的时序上下文
- **结构化事实（Facts）**：以图节点形式存储关键信息
- **灵活链接**：通过边连接相关的事实和片段，支持多跳推理

### 3. Agentic 检索器（Agentic Retriever）

在线推理阶段，采用具备工具的 Agent 检索器：
- **迭代检索**：不是一次性返回结果，而是多轮探索记忆图谱
- **工具多样化**：提供不同工具（如查找、比较、推理链构建等）
- **显式推理**：能够对记忆内容进行推理，而非仅做相似度匹配

### 4. 基准测试表现

在四个情景记忆基准测试中全面超越现有方法：
- 相比 Mem0 和 HippoRAG 2，REMem 在情景回忆任务上提升 3.4%
- 在情景推理任务上提升 13.4%
- 对无法回答的问题具有更强的拒绝能力（更稳健的拒答行为）

## 为什么重要

这篇论文指出了一个关键问题：当前 Agent 的记忆大多是"语义记忆"（存储事实），而缺乏"情景记忆"（存储经历并能回忆和推理）。REMem 填补了这一空白，将事件建模、时序感知和 Agentic 检索三者结合，对推动具有真正记忆能力的 AI Agent 具有重要意义。

## 与移动端/端侧的相关性

论文聚焦于通用语言 Agent，但其两阶段架构（离线索引 + 在线推理）对端侧部署有启发：离线索引可以预计算，在线推理阶段则可以根据设备能力动态调整工具使用的复杂度和检索深度。

## 参考文献

（参考文献待从原文补充）
