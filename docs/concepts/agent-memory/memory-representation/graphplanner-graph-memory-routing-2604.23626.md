---
title: "GraphPlanner: Graph Memory-Augmented Agentic Routing for Multi-Agent LLMs"
arXiv: 2604.23626
date: 2026-04-21
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Tao Feng, Haozhen Zhang, Zijie Lei, Peixuan Han, Jiaxuan You
- **提交日期**: 2026-04-21

## 摘要

LLM routing has achieved promising results in integrating the strengths of diverse models while balancing efficiency and performance. However, existing routing strategies rely on single-turn classification or semantic similarity, ignoring the rich relational structure among tasks. GraphPlanner introduces a Graph Memory architecture that captures task dependencies and agent capabilities as a bipartite graph. Nodes represent tasks and agent capabilities; edges encode prerequisite relationships and suitability scores. The router uses graph neural networks to propagate information across the task-agent graph, enabling it to predict not just which agent is best for the current task, but also what downstream tasks will follow and which agent should prepare for them.

## 核心贡献

1. **二部图记忆架构**: 节点代表任务和能力，边缘编码前置关系和适合度分数
2. **图神经网络路由**: 跨任务-能力图传播信息，预测当前任务和下游任务
3. **前瞻路由**: 考虑任务依赖链而非孤立决策

## 为什么重要

首次将任务依赖关系引入多 Agent 路由，使路由决策具有前瞻性，避免了单步分类的短视问题。

## 与端侧/移动端的相关性

GNN 计算较重，端侧部署需要图简化或使用轻量图注意力机制。适用于边缘服务器级别的多 Agent 编排。
