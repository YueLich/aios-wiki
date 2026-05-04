---
title: "CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering"
arXiv: 2604.26176
date: 2026-04-28
authors: ["Yushi Sun", "Lei Chen"]
tags: [agent-memory, memory-retrieval, RAG, KGQA, semantic-caching]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.26176
- **作者**: Yushi Sun, Lei Chen
- **提交日期**: 2026-04-28
- **方向**: 记忆检索 / RAG / 知识图谱问答

## 摘要（全文翻译）

大语言模型（LLM）与检索增强生成（RAG）的结合显著推进了知识图谱问答（KGQA）。然而，现有 LLM 驱动的 KGQA 系统是**无状态的规划器**，在生成检索规划时孤立运作，无法利用历史查询模式——类似于数据库系统每次查询都从零优化而没有计划缓存。这一根本设计缺陷导致**模式幻觉（schema hallucinations）**和有限的检索覆盖率。

CacheRAG 提出了一个系统的**缓存增强架构**，将无状态查询规划转变为**缓存感知的范式**。CacheRAG 维护一个多级语义缓存，捕获历史查询模式、规划和检索结果，支持跨相关查询的计算复用。

核心洞察：KGQA 查询展现出显著的**时间和结构局部性**——用户在会话内倾向于询问相关实体和关系。通过利用这种局部性，CacheRAG 减少了冗余的 LLM 调用，提高了检索一致性，并通过缓存计划复用缓解了模式幻觉。

## 核心贡献

1. **问题定义**：指出现有 KGQA 系统的无状态缺陷——每次查询从零开始，缺少计划缓存
2. **CacheRAG 架构**：三级设计原则：
   - **模式无关的用户接口**：通过中间语义表示（ISR）的两阶段语义解析，使用户纯用自然语言交互，后端适配器将 LLM 与本地模式上下文连接，编译可执行的物理查询
   - **多样性优化的缓存检索**：两层层级索引（Domain → Aspect）配合最大边际相关性（MMR），最大化缓存示例的结构多样性，缓解推理同质化
   - **有界启发式扩展**：确定性深度和广度的子图操作符，带有严格复杂度保证，在不冒无界 API 执行风险的情况下显著提高检索召回率
3. **实验结果**：在 CRAG 数据集上准确率提升 +13.2%，真实性提升 +17.5%

## 为什么重要

这篇论文将数据库领域的**计划缓存（plan caching）**概念引入 LLM 记忆检索。传统 RAG 每个查询独立生成检索计划，CacheRAG 则利用会话局部性复用历史检索计划——这对 Agent 的长对话记忆系统有直接启发：记忆检索不应只看语义相似性，还应考虑**查询结构的历史复用**。

## 与端侧/移动端的相关性

CacheRAG 的有界子图操作符和层级缓存设计对**资源受限的端侧部署**有参考价值。移动端 Agent 的知识图谱查询可以通过本地缓存历史查询计划来减少每次查询的计算量，避免重复调用云端 LLM 做相同的子图展开。

## 关键引文

> "existing LLM-driven KGQA systems act as stateless planners, generating retrieval plans in isolation without exploiting historical query patterns: analogous to a database system that optimizes every query from scratch without a plan cache"

---

## 方法细节

### 两阶段语义解析

ISR（Intermediate Semantic Representation）将用户自然语言查询转换为结构化语义表示，再由后端适配器根据本地 KG 模式编译为可执行物理查询。这解决了两个问题：
- 用户不需要了解 KG 模式即可提问
- LLM 输出可安全落地为结构化操作

### 多级语义缓存

```
Session Cache (短期)
  └── Domain-Level Cache (中层)
        └── Aspect-Level Cache (细粒度)
```

### MMR 检索

最大边际相关性在缓存示例选择时平衡相关性和多样性，避免系统总是返回高度相似的历史案例，减少推理路径同质化。
