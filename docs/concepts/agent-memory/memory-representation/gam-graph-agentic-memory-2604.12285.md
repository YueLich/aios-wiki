---
title: "GAM: Graph Agentic Memory"
arXiv: 2604.12285
date: 2026-04-14
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# GAM: Graph Agentic Memory

## 论文基本信息

- **作者**: Chenxu Wang, et al.
- **arXiv**: https://arxiv.org/abs/2604.12285
- **领域**: cs.AI, cs.MA

## 摘要

GAM 提出用图结构作为 Agent 记忆的表示基础，将 Agent 的交互历史建模为异构图，节点类型包括实体、动作、时间戳、环境状态等，边类型包括因果关系、时序关系、语义相似关系等。图结构使 Agent 能够进行多跳推理和路径搜索，支持复杂的记忆查询（如"找出所有在咖啡店发生且涉及我的动作"）。GAM 在多跳推理和反事实推理任务上显著优于平面记忆基线。

## 核心贡献

1. **Graph-based Memory Representation**: 首个全面使用图结构作为 Agent 记忆表示的框架
2. **Heterogeneous Memory Graph**: 异构图包含多种节点和边类型
3. **Multi-hop Reasoning**: 支持多跳推理和路径搜索
4. **Counterfactual Reasoning**: 支持反事实记忆推理
5. **显著性能提升**: 多跳推理和反事实任务上显著优于平面记忆

## 研究背景与问题

平面文本记忆（如向量存储）无法表达实体间的复杂关系，导致多跳推理和反事实推理困难。图结构记忆是解决这一问题的自然方案。

## 核心方法

1. **Memory Graph Construction**: 从 Agent 交互历史自动构建记忆图
2. **Heterogeneous Node/Edge Types**: 实体、动作、时间、环境等多种节点/边类型
3. **Graph Neural Memory Reader**: 图神经网络记忆读取器
4. **Query-to-Graph Matching**: 将自然语言查询转换为图查询
5. **Path-based Retrieval**: 基于路径的复杂记忆检索

## 为什么重要

GAM 将知识图谱领域的图表示技术系统性地引入 Agent 记忆，为复杂记忆推理提供了结构化基础。对需要多跳推理能力的 Agent（如研究助手、分析师）有重要价值。

## 与移动端/端侧相关性

1. **图结构紧凑性**: 图结构比平面文本更紧凑，适合端侧存储
2. **GNN 高效变体**: 移动端可使用轻量级 GNN 变体
3. **复杂查询支持**: 移动端 Agent 需要支持复杂记忆查询
4. **隐私保护**: 图结构支持细粒度的记忆访问控制
