---
title: Beyond Similarity Search: Tenure and the Case for Structured Belief State in LLM Memory
arXiv: 2605.11325
date: 2026-05-11
tags: [agent-memory, memory-retrieval, belief-state, structured-memory]
reviewer: auto
source: arXiv RSS/API
---

# 概要

跨会话记忆是 LLM 智能体的核心挑战。现有方法将记忆存储为向量，通过语义相似性检索——但这本质上是一个**搜索问题**，而非**状态管理问题**。本文提出 **Tenure**，一个本地优先（local-first）的代理维护结构化信念存储的方案。Tenure 核心创新：带认知状态的类型化信念存储（typed belief store with epistemic status）、版本化supersession 和范围隔离（scope isolation），通过精度优先检索（precision-first retrieval）向每次 LLM 会话注入精选上下文。

# 核心贡献

## 1. 问题诊断：搜索 vs. 状态管理
论文的核心论点是：**跨会话记忆是状态管理问题，而非搜索问题**。

相似性搜索失败的根因：
- 命名实体解析在有界词汇表场景中失败：同一用户关于共享技术领域的信念在语义上天然接近
- 单用户是最简单的有界词汇表上下文；工程团队通过共享代码库和术语收敛到相同属性

## 2. Tenure 的结构化信念存储

### 类型化 Schema
每个信念（Belief）包含：
- **内容**：提取的事实
- **why_it_matters 字段**：将原始事实转换为可操作指令，而非供模型重新推导的原始材料
- **epistemic status**：信念的认知状态（已知、未知、更新等）
- **scope isolation**：范围隔离，授权边界内保证正确的信念被使用

### 版本化 Supersession
信念随时间更新时，旧版本被保留而非删除，支持追溯和审计。

## 3. 检索机制：精度优先

### Alias-Weighted BM25 vs. Dense Embeddings
| 方法 | 平均精度 | 案例通过率 |
|------|----------|------------|
| Cosine 相似度（dense） | 0.12 | 8/72 |
| Alias-weighted BM25 | 1.0 | 72/72 |

### Alias Enrichment Flywheel
- 查询作者和信念作者是同一人（单一用户场景）
- 别名富化飞轮持续索引用户特定词汇
- 解决了不同作者间的词汇不匹配问题

### 多轮话题漂移评估
在噪声关键轮次上：
- 向量后端漂移分数 0.43–0.50
- BM25 保持稳定

## 4. 硬范围隔离（Hard Scope Isolation）
提供结构性保证：
- 正确的信念被使用
- 仅在用户授权的边界内使用

## 5. 与相似性搜索的根本区别

| 维度 | 相似性搜索 | Tenure |
|------|------------|--------|
| 核心抽象 | 向量嵌入 | 类型化信念 |
| 匹配方式 | 语义相似 | 词汇精确 |
| 状态管理 | 无 | 有（版本、supersession）|
| 认知建模 | 无 | 有（epistemic status）|

# 为什么重要

论文挑战了 RAG 作为跨会话记忆主流范式的假设：
- **RAG 是搜索，不是状态**：存储-嵌入-检索的范式天然不适合需要精确命名的场景
- **结构化信念优于平面向量**：typed schema + why it matters 直接将事实转化为行动
- **BM25 被低估**：在单一用户有界词汇表场景，BM25 优于dense embeddings

# 与移动端/端侧相关性

Tenure 的本地优先设计对端侧友好：
- 所有数据存储在本地，无需云端同步
- BM25 计算轻量，适合资源受限设备
- 结构化信念的版本化支持离线场景
- 范围隔离提供了隐私保护的结构性保证
