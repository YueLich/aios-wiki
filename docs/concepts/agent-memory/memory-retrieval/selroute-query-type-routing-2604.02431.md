---
title: "SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval"
arXiv: 2604.02431
date: 2026-04-02
authors: ["Matthew McKee"]
tags: [agent-memory, memory-retrieval, query-routing, lexical-search, semantic-search, edge-AI]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.02431
- **作者**: Matthew McKee
- **提交日期**: 2026-04-02
- **方向**: 记忆检索 / 查询类型路由 / 混合检索
- **发布**: 12页，12表，3附录

## 摘要（全文翻译）

从长期会话记忆中检索相关过去交互通常依赖大型密集检索模型（110M-1.5B参数）或 LLM 增强索引。本文提出 **SelRoute**，一个根据查询类型将每个查询路由到专门检索流程的框架——包括词汇检索、语义检索、混合检索或词汇增强检索。

在 LongMemEval_M 上，SelRoute 使用 bge-base-en-v1.5（109M参数）达到 **Recall@5 = 0.800**，使用 bge-small-en-v1.5（33M参数）达到 **0.786**，对比使用 LLM 生成事实键的 Contriever 为 0.762。一个零 ML 基线仅使用 SQLite FTS5 就达到了 **NDCG@5 = 0.692**，超过所有已发布的排序质量基线——这一差距部分归因于词汇检索实现差异。五折分层交叉验证确认路由稳定性（CV gap 1.3-2.4 Recall@5 点；6种查询类型中4种的路由稳定）。

基于正则表达式的查询类型分类器达到 **83% 有效路由准确率**，端到端检索（预测类型，Recall@5 = 0.689）仍优于统一基线。在8个额外基准（涵盖62,000+实例——包括 MSDialog、LoCoMo、QReCC 和 PerLTQA）上的跨基准评估确认了泛化能力，无需基准特定调优。同时暴露了在推理密集型检索上的明确失败模式（RECOR Recall@5 = 0.149），限制了其适用范围。另一个发现是**检索-嵌入不对称性**：存储时的词汇扩展改善了词汇搜索但恶化了嵌入搜索，启示需要针对每个管道独立做存储决策。

**整个系统不需要 GPU、不需要 LLM 推理**。

## 核心贡献

1. **查询类型路由**：根据查询的词汇/语义/混合性质路由到最优检索管道，而非统一使用语义检索
2. **超轻量实现**：SQLite FTS5 零 ML 基线已超过所有已发布基线；33M 参数模型即可达到 SOTA
3. **混合检索解耦**：存储时词汇增强会伤害嵌入搜索——启示存储和检索策略应独立优化
4. **无 GPU/LLM 推理**：适合端侧部署

## 为什么重要

SelRoute 的核心发现是：**不是所有记忆查询都适合语义检索**。某些查询（如精确事实查找）用简单的 SQLite FTS5 词汇检索效果更好，语义检索反而引入噪声。这对端侧记忆系统的设计有重要启示：

- **混合存储策略**：同时维护词汇索引和语义索引，按查询类型选择
- **路由轻量化**：Regex 分类器（83%准确率）即可路由，不需要重型 LLM
- **存储-检索不对称**：存储时的增强决策不一定对检索有益，需独立评估

## 与端侧/移动端的相关性

**强相关**。SelRoute 整个系统不需要 GPU、不需要 LLM 推理，非常适合移动端/可穿戴设备。33M 参数的 bge-small 模型完全可以跑在手机端，结合 SQLite FTS5 的词汇检索，可以在离线状态下提供高质量的会话记忆检索。

## 关键引文

> "A zero-ML baseline using SQLite FTS5 alone achieves NDCG@5 of 0.692, already exceeding all published baselines on ranking quality"

> "enrichment-embedding asymmetry: vocabulary expansion at storage time improves lexical search but degrades embedding search, motivating per-pipeline enrichment decisions"

---

## 方法细节

### 四种检索管道

1. **Lexical（FTS5）**：精确关键词匹配
2. **Semantic（dense embedding）**：向量相似度
3. **Hybrid**：结合词汇和语义
4. **Vocabulary-enriched**：存储时做词汇扩展

### 查询类型分类器

基于正则表达式的轻量分类器，将查询分为：
- 事实查找型（适合词汇）
- 推理型（适合语义/混合）
- 主题探索型（适合混合）
等类别

### 存储-检索不对称

存储时对文本做词汇增强（如同义词扩展）可以增加召回，但对嵌入向量产生负面影响。这意味着存储管道和检索管道需要**独立优化**，不能假设存储时的优化对检索也有益。
