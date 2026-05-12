---
title: "HAGE: Harnessing Agentic Memory via RL-Driven Weighted Graph Evolution"
arXiv: "2605.09942"
date: "2026-05-11"
tags: [agent-memory, memory-retrieval, weighted-graph, reinforcement-learning]
reviewer: auto
source: arXiv API
---

# HAGE: Harnessing Agentic Memory via RL-Driven Weighted Graph Evolution

## 摘要

现有 Agent 记忆检索多采用静态查表（向量相似度搜索或固定二元关系图），无法建模关系强度、置信度和查询依赖的相关性差异。本文提出 **HAGE**（RL-Driven Weighted Graph Evolution），将记忆检索重新建模为在统一关系记忆图上的**序列式、查询条件化遍历**。记忆节点共享，关系构建专属图视图，每条边关联可学习的**关系特征向量**。给定查询时，LLM 分类器识别关系意图，路由网络动态调制边嵌入的对应维度，遍历分数结合语义相似度与查询条件化边表示联合计算。

## 核心贡献

1. **加权多关系记忆框架**：边关联多维关系特征向量，而非固定布尔标签，支持建模关系强度和置信度差异。
2. **查询条件化动态遍历**：关系意图由 LLM 分类器识别，路由网络根据查询调制边嵌入维度，实现软性抑制噪声关系、优先高效用关系路径。
3. **RL 联合训练框架**：联合优化路由行为和边表示，用下游任务信号驱动，无需人工设计关系类型。
4. **精度-效率权衡优势**：实验表明长时推理精度提升，且相比 SOTA 记忆系统有更好的效率权衡。

## 为什么重要

当前 Agent 记忆系统的核心瓶颈在于**关系建模不足**——向量检索无法捕捉事件间的结构化关联，固定图结构无法适应不同查询的语义重心。HAGE 通过可学习的加权关系图和 RL 驱动演化，首次将记忆检索从"最近邻查表"推进到"图上推理遍历"，为多跳推理和复杂关系推理提供了新范式。

## 与移动端/端侧相关性

论文未明确聚焦移动端，但加权图遍历的稀疏激活特性（只遍历高权重路径）使其具备端侧部署潜力——无需全量扫描记忆，适合资源受限的本地 Agent 场景。

## 参考文献

- HAGE GitHub: https://github.com/FredJiang0324/HAGE_MVPReview
