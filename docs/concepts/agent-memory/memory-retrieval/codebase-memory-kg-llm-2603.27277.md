---
title: "Codebase-Memory: Tree-Sitter-Based Knowledge Graphs for LLM Code Exploration via MCP"
arXiv: 2603.27277
date: 2026-03-28
tags: [agent-memory, memory-representation, knowledge-graph, code-agent]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **作者**: Martin Vogel, Falk Meyer-Eschenbach, Severin Kohler, Elias Grünewald, Felix Balzer
- **类别**: cs.SE (Software Engineering)
- **发表**: 2026-03-28

## 摘要

大型语言模型（LLM）代码 Agent 通常通过重复读取文件和 grep 搜索来探索代码库，每次查询消耗数千 tokens 且缺乏结构化理解。

本文提出 **Codebase-Memory**，一个通过模型上下文协议（MCP）构建持久化 Tree-Sitter 知识图谱的开源系统。系统通过多阶段 pipeline 解析 66 种编程语言，包含并行 worker pool、调用图遍历、影响分析和社区发现。

在 31 个真实代码库上的评估表明：Codebase-Memory 以 83% 的答案质量（对比文件探索 Agent 的 92%）实现了：
- **10 倍更少的 tokens 消耗**
- **2.1 倍更少的工具调用次数**

对于图原生查询（如 hub 检测和调用者排名），系统在 19/31 种语言上匹配或超越探索式 Agent。

## 核心贡献

1. **Tree-Sitter 知识图谱**：基于 MCP 协议的持久化知识表示，支持 66 种语言
2. **多阶段解析 pipeline**：并行 worker pools、调用图遍历、影响分析、社区发现
3. **结构化代码理解**：超越文本搜索的语义级代码关系建模
4. **高效检索**：图原生查询显著减少 token 消耗和工具调用次数

## 为什么重要

传统代码探索方式的瓶颈：
- 每次查询消耗数千 tokens，成本高昂
- 缺乏代码结构理解，无法回答"哪个文件最重要"等结构化问题
- 工具调用次数多，延迟高

Codebase-Memory 通过持久化知识图谱实现：
- 将代码结构（调用关系、依赖关系、社区结构）显式存储
- 支持复杂的结构化查询（hub 节点、影响范围、社区划分）
- 大幅降低 token 消耗和工具调用延迟

## 与端侧/移动端的相关性

移动端代码 Agent 面临更严格的资源约束：
- 知识图谱可增量更新，无需每次重新解析代码库
- 减少与云端 LLM 的交互次数和 token 消耗
- 支持离线代码分析（知识图谱可本地存储）

## 参考文献

（参考文献待从原文补充）
