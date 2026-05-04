---
title: "CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering"
arXiv: 2604.26176
date: 2026-04-28
tags: [memory-retrieval, RAG, knowledge-graph]
reviewer: auto
source: arXiv RSS/API
---

# CacheRAG: A Semantic Caching System for Retrieval-Augmented Generation in Knowledge Graph Question Answering

## 论文基本信息

- **arXiv ID**: 2604.26176
- **作者**: Yushi Sun, Lei Chen
- **提交日期**: 2026-04-28
- **类别**: cs.DB, cs.CL

## 摘要

LLM 与检索增强生成（RAG）的集成为知识图谱问答（KGQA）带来了显著进展。然而现有 LLM 驱动的 KGQA 系统作为无状态规划器，孤立地生成检索计划而不利用历史查询模式——类似于数据库系统每次从头优化每个查询而不使用计划缓存。这种根本性设计缺陷导致模式幻觉和检索覆盖受限。论文提出 CacheRAG，一种为 LLM KGQA 量身定制的缓存增强架构，将无状态规划器转变为持续学习器。CacheRAG 引入三个为 LLM 场景设计的新原则：模式无关用户界面（ISR 中间语义表示两阶段框架）、语义缓存（超越频率优化）、适应性检索计划复用。

## 核心贡献

1. **持续学习者转型**：从无状态到有状态的 KGQA 规划器，类比数据库计划缓存。
2. **ISR 中间语义表示**：两阶段语义解析框架，让非专业用户用自然语言交互同时保持后端结构化。
3. **语义缓存**：不只是按频率缓存，而是理解查询的语义相似性进行缓存复用。
4. **检索计划复用**：跨历史查询复用检索计划，减少重复推理开销。

## 为什么重要

CacheRAG 将数据库领域的成熟技术（计划缓存、成本优化）引入 LLM+RAG 场景，开创了「LLM 查询缓存」这一新方向。传统 RAG 每个查询都重新生成检索计划，CacheRAG 通过学习历史模式实现增量推理。对移动端知识库问答的启示：移动端 App 帮助系统、法律顾问等知识密集型应用可从语义缓存中大幅降低推理成本。

## 与移动端/端侧相关性

- 移动端知识库问答（App 使用帮助、设备设置指南）可受益于语义缓存减少 token 消耗
- ISR 模式无关接口对隐私敏感场景有优势（用户自然语言查询，后端不暴露知识库结构）
- 语义缓存可本地化部署在端侧，减少对云端 API 的依赖
