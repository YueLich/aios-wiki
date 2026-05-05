---
title: "ContextWeaver: Selective and Dependency-Structured Memory Construction for LLM Agents"
arXiv: 2604.23069
date: 2026-04-18
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Yating Wu, Yuhao Zhang, Sayan Ghosh, Sourya Basu, Anoop Deoras, Jun Huan, Gaurav Gupta
- **提交日期**: 2026-04-18

## 摘要

LLM agents often struggle in long-context interactions. As the agent accumulates more interaction history, context management approaches such as sliding window and prompt compression lose critical dependencies. ContextWeaver proposes a selective memory construction approach that explicitly models variable dependencies across conversation turns. The key insight is that not all conversation turns are equally important—some establish preconditions or constraints that constrain future actions, while others are incidental. ContextWeaver builds a dependency graph where nodes are conversation turns and edges encode prerequisite, elaboration, and contradiction relationships. Memory construction then becomes a graph traversal problem: which turns must be retained to maintain all critical dependencies?

## 核心贡献

1. **依赖图建模**: 边缘编码前置、阐述和矛盾关系，而非简单的时间序列
2. **选择性记忆构建**: 图遍历问题——保留哪些 turn 以维持所有关键依赖
3. **子图检索**: 返回相关 turns 及其依赖子图，而非扁平列表

## 为什么重要

解决了滑动窗口和提示压缩丢失关键依赖的根本问题。ContextWeaver 使得 Agent 能够追踪因果链，而不仅仅是时间上相近的事件。

## 与端侧/移动端的相关性

**高度端侧相关**：依赖图可高效维护，只需存储关键节点和边缘，比完整对话历史小得多。在资源受限设备上优势明显。
