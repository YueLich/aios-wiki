---
title: "Thought-Retriever: Don't Just Retrieve Raw Data, Retrieve Thoughts for Memory-Augmented Agentic Systems"
arXiv: "2604.12231"
date: "2026-04-14"
tags: [agent-memory, memory-retrieval, retrieval-augmented-memory]
reviewer: auto
source: arXiv RSS/API
---

# Thought-Retriever: Don't Just Retrieve Raw Data, Retrieve Thoughts for Memory-Augmented Agentic Systems

## 摘要

大语言模型虽已具备强大内部能力，但仍然难以有效整合海量外部知识。传统检索增强 LLM 仅能从外部知识库中检索 top-K 原始数据块，受限于上下文长度。本文提出 Thought-Retriever，一种新颖的模型无关算法，帮助 LLM 在不受上下文长度或检索数据块数量约束的情况下，基于任意长的外部数据生成输出。其核心思想是让 LLM 充分利用解决历史用户查询时生成的中间响应（思想），过滤无意义和冗余的思想，在思想记忆中组织它们，并在处理新查询时检索相关思想。这有效地为基于 LLM 的 Agent 配备了自我进化的长期记忆。

## 核心贡献

1. **思想记忆（Thought Memory）**：将 LLM 的中间响应（思想）作为记忆单元，比原始数据块更具信息密度和语义相关性

2. **自我进化机制**：证明 Thought-Retriever 可帮助 LLM 在解决更多用户查询后实现自我进化

3. **深度思想利用**：学习利用更深层的思想来回答更抽象的用户查询

4. **学术评估基准 AcademicEval**：构建了需要 LLM 利用超长上下文回答真实学术论文查询的评估基准

5. **显著性能提升**：在多个任务上平均 F1 分数提升至少 7.6%，胜率提升 16%

## 为什么重要

Thought-Retriever 突破了传统 RAG 的核心瓶颈——上下文长度限制。通过将 LLM 的中间推理过程作为记忆内容，实现了：

- **无限上下文**：不再受限于 LLM 的上下文窗口
- **自我进化**：记忆随使用不断优化，而非静态存储
- **语义浓缩**：思想比原始数据更富含语义信息

这为构建真正意义的学习型 Agent 提供了新范式。

## 与移动端/端侧相关性

1. **端侧知识管理**：移动端 Agent 可利用思想记忆管理本地知识库
2. **增量学习**：思想记忆支持在边缘设备上持续学习
3. **资源受限场景**：思想压缩比原始数据更适合存储受限的移动设备
4. **隐私保护**：本地生成的思想比原始数据更适合保留在设备上

## 相关论文

- MemReranker (2605.06132) 推理感知重排的 Agent 记忆检索
- ScrapMem (2605.03804) 端侧个性化记忆的光学遗忘框架
- RAG-Memory (2512.02333) 在线学习的检索增强记忆
