---
title: PersonalAI 2.0: Enhancing Knowledge Graph Traversal/Retrieval with Planning Mechanism for Personalized LLM Agents
arXiv: 2605.13481
date: 2026-05-13
tags: [agent-memory, memory-representation, knowledge-graph, personalized-agent, graph-rag]
reviewer: auto
source: arXiv RSS/API
---

# PersonalAI 2.0: Enhancing Knowledge Graph Traversal/Retrieval with Planning Mechanism for Personalized LLM Agents

## 论文信息

- **arXiv**: 2605.13481
- **作者**: Mikhail Menschikov, Matvey Iskornev, Alexander Kharitonov, Alina Bogdanova, Mikhail Belkin, Ekaterina Lisitsyna, Artyom Sosedka, Victoria Dochkina, Ruslan Kostoev, Ilya Perepechkin, Evgeny Burnaev
- **发表日期**: 2026-05-13
- **类别**: cs.CL
- **主题**: 知识图谱增强的个性化 Agent 记忆系统

## 摘要

PersonalAI 2.0 (PAI-2) 是一个将外部知识图谱（Knowledge Graph, KG）与大语言模型深度集成的框架，旨在增强个性化 LLM Agent 的记忆与推理能力。该框架针对现有 GraphRAG 方法的局限性，提出了动态多阶段查询处理流水线，能够执行自适应、迭代式信息搜索。

## 核心贡献

1. **动态多阶段查询处理**：PAI-2 能够根据提取的实体、匹配的图节点和生成的线索查询，执行自适应迭代式信息搜索，而非一次性检索
2. **图遍历算法增强**：BeamSearch、WaterCircles 等图遍历算法相比扁平化检索器平均提升 6%
3. **搜索计划增强机制**：启用搜索计划增强后，在六个数据集上获得 18% 的 LLM-as-Judge 评分提升
4. **MINE-1 基准 SOTA**：在个性化记忆信息保留基准上达到 89% 的信息保留分数

## 技术详解

### 问题背景

现有的 GraphRAG 方法存在以下局限：
- 缺乏自适应迭代搜索能力
- 无法根据中间结果动态调整查询策略
- 图遍历深度受限，难以处理复杂多跳查询

### 框架设计

PAI-2 的核心设计：

1. **实体提取**：从用户查询中提取关键实体
2. **图顶点匹配**：将实体与知识图谱中的顶点匹配
3. **线索查询生成**：基于匹配结果生成下一步搜索的线索
4. **迭代搜索**：通过 BeamSearch 或 WaterCircles 算法遍历图谱
5. **答案生成**：整合检索结果生成最终答案

### 性能评估

在六个基准上的表现（对比 LightRAG、RAPTOR、HippoRAG 2）：
- Natural Questions、TriviaQA、HotpotQA、2WikiMultihopQA、MuSiQue、DiaASQ
- LLM-as-Judge 平均提升 4%
- 图遍历算法平均提升 6%
- 搜索计划机制带来 18% 提升

### 记忆信息保留

在 MINE-1 基准上：
- 89% 信息保留分数（SOTA）
- 使用 7-14B 参数的 LLM 即可达成

## 为什么重要

PersonalAI 2.0 展示了知识图谱作为 Agent 外部记忆的有效性：
- **可解释性强**：图结构提供了透明的推理路径
- **迭代式记忆检索**：通过 clue-queries 实现自适应搜索，而非静态检索
- **个性化记忆**：针对每个用户的知识图谱进行定制
- **减少幻觉**：通过精确的图遍历而非端到端生成，提高事实正确性

## 与端侧/移动端的相关性

- **可部署性强**：PAI-2 的框架设计适合在端侧部署——知识图谱可本地存储，图遍历计算量相对可控
- **隐私友好**：个性化知识图谱可以在设备端构建和查询，用户数据不出本地
- **高效检索**：相比全量上下文输入，图遍历的线性时间复杂度更适合资源受限的端侧环境
- **模块化设计**：各组件（实体提取、图匹配、线索生成）均可独立优化，便于在移动端裁剪

## 参考文献

（参考文献待从原文补充）
