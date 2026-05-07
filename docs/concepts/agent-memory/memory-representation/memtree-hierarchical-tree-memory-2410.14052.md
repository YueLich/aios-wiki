---
title: From Isolated Conversations to Hierarchical Schemas - Dynamic Tree Memory Representation for LLMs
arXiv: 2410.14052
date: 2024-10-17
tags: [agent-memory, memory-representation, hierarchical-memory]
reviewer: auto
source: arXiv API
---

# MemTree: Dynamic Tree Memory Representation for LLMs

## 摘要

尽管大模型的上下文窗口不断扩大，但有效的长期记忆管理仍面临挑战。本文提出 MemTree，一种利用动态树结构记忆表征来优化信息组织、检索和整合的算法，灵感来自人类认知schemas。MemTree 以层次化方式组织记忆，每个节点封装聚合的文本内容、对应语义嵌入和活跃时间戳，支持基于时间的记忆衰减和基于相关性的检索。

## 核心贡献

1. **动态树结构记忆**：层次化组织 LLM 的对话/知识记忆
2. **认知启发的节点设计**：每个节点封装文本+嵌入+时间戳
3. **基于时间的自然遗忘**：通过时间衰减使旧记忆逐渐淡化
4. **语义+时序双路检索**：既可按语义相似度也可按时间顺序检索
5. **无需额外训练**：即插即用地增强现有 LLM

## 技术方法

### 树结构组织
- 根节点：全局概览
- 中间节点：主题/会话聚类
- 叶节点：具体事实/对话片段
- 边：语义/时序关联

### 节点结构
每个记忆节点包含：
- **聚合文本**：节点内所有记忆的摘要
- **语义嵌入**：用于相似度检索
- **活跃时间戳**：支持基于时间的操作
- **子节点指针**：支持层次遍历

### 检索与整合
- 语义检索：找到与查询最相关的节点路径
- 时序检索：找到特定时间段的相关记忆
- 跨层级整合：聚合多个节点的信息回答复杂查询

## 为什么重要

MemTree 是"层次化记忆"在 LLM 应用中的成功实践。相比扁平的向量记忆，树结构能捕捉记忆之间的层级关系和逻辑结构，对需要复杂推理的 Agent 系统更有价值。这条路线的后续发展（如 AutoMemory、ChatMemory）证明了层次化记忆的重要性。

## 与移动端/端侧相关性

1. **移动端个性化记忆**：组织用户的日常交互历史
2. **低内存开销**：层次化压缩比扁平向量更节省空间
3. **增量更新**：新记忆可以高效插入现有树结构
4. **可解释性**：树结构提供更可解释的记忆检索路径

## 参考文献

- Alireza Rezazadeh, Zichao Li, Wei Wei, Yujia Bao. "From Isolated Conversations to Hierarchical Schemas: Dynamic Tree Memory Representation for LLMs." arXiv:2410.14052, 2024.
