---
title: "SelRoute: Query-Type-Aware Routing for Long-Term Conversational Memory Retrieval"
arXiv: 2604.02431
date: 2026-04-02
tags: [agent-memory, memory-retrieval, query-routing, lightweight]
reviewer: auto
source: arXiv API
authors: "Matthew McKee"
---

## 论文信息

- **arXiv**: 2604.02431
- **发表日期**: 2026-04-02
- **作者**: Matthew McKee
- **方向**: 记忆检索与路由

## 摘要

从长期对话记忆中检索相关过去交互通常依赖大型稠密检索模型（110M-1.5B 参数）或 LLM 增强索引。本文提出 SelRoute，一个根据查询类型将每个查询路由到专门检索 pipeline（词汇检索、语义检索、混合检索或词汇丰富检索）的框架。在 LongMemEval_M 上，SelRoute 使用 bge-base-en-v1.5（109M 参数）达到 Recall@5=0.800，使用 bge-small-en-v1.5（33M 参数）达到 0.786，而使用 LLM 生成事实键的 Contriever 为 0.762。一个基于 SQLite FTS5 的零 ML 基线就能达到 NDCG@5=0.692，超越所有已发布基线的排序质量。五折分层交叉验证确认路由稳定性（CV 差距 1.3-2.4 Recall@5 分；6 种查询类型中 4 种的路由稳定）。基于正则表达式的查询类型分类器达到 83% 的有效路由准确率，在预测类型上进行端到端检索（Recall@5=0.689）仍优于均匀基线。在 8 个额外基准的跨基准评估（涵盖 62,000+ 实例）——包括 MSDialog、LoCoMo、QReCC 和 PerLTQA——确认了无需基准特定调优的泛化能力，同时暴露了推理密集型检索上的明显失败模式（RECOR Recall@5=0.149）。本文还识别了一种富文本嵌入非对称性：存储时的词汇扩展改善词汇搜索但损害嵌入搜索，催生了每个 pipeline 独立决策的富文本策略。整个系统检索时无需 GPU 和 LLM 推理。

## 核心贡献

1. **查询类型路由**：根据查询类型（事实型、推理型、闲聊型等）动态选择最优检索 pipeline
2. **零 ML 基线强大**：SQLite FTS5 alone 就能超越所有已发布基线，说明简单方法被低估
3. **无需 GPU/LLM**：整个系统在消费级硬件上运行，降低部署门槛
4. **富文本嵌入非对称性发现**：存储时做词汇扩展对词汇搜索有利但对嵌入搜索有害——需要分别优化

## 为什么重要

对话记忆的检索需要处理多种类型查询——有些需要精确词汇匹配，有些需要语义理解，有些需要混合策略。SelRoute 证明了"为不同查询类型选择不同检索方法"比"用单一方法应对所有查询"更有效。这对端侧记忆系统特别重要——路由到轻量方法（如纯词汇搜索）可以避免不必要的计算开销。

### 与移动端/端侧的相关性

- **无需 GPU/LLM**：33M 参数模型可在移动端运行
- **SQLite FTS5** 是嵌入式数据库的标配，零依赖
- **按需路由**策略天然适配资源受限的端侧场景
