---
title: "SmartSearch: How Ranking Beats Structure for Conversational Memory Retrieval"
arXiv: "2603.15599"
date: "2026-03-16"
tags: [agent-memory, memory-retrieval, conversational-memory]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

SmartSearch 挑战了对话记忆系统的主流范式——即需要在摄取时做 LLM 结构化、查询时用学习式检索策略。论文证明：**两者都不必要**。

**核心发现**：
- 从原始非结构化对话历史中检索，完全deterministic的pipeline即可达到SOTA
- **NER加权的子串匹配**负责召回（recall）
- **规则化实体发现**负责多跳扩展
- **CrossEncoder + ColBERT rank fusion**是唯一的学习组件，且在 CPU 上 ~650ms 即可完成

**Oracle 分析**揭示了编译瓶颈：检索召回率达到 98.6%，但没有接口化（compilation）时整体性能受限。

## 为什么重要

这篇论文是对"复杂即更好"范式的根本性挑战。在 memory retrieval 领域，学术界倾向于设计越来越复杂的架构，但 SmartSearch 证明简单、确定性的方法配合高效排序即可超越复杂的 LLM-based 结构化和 learned retrieval policies。

## 与端侧/移动端的相关性

**高度相关**。SmartSearch 的 pipeline 完全在 CPU 上运行（~650ms），不依赖 GPU。这对移动端部署极其友好——无需昂贵 GPU 即可部署高质量对话记忆检索系统。

## 摘要

Recent conversational memory systems invest heavily in LLM-based structuring at ingestion time and learned retrieval policies at query time. We show that neither is necessary. SmartSearch retrieves from raw, unstructured conversation history using a fully deterministic pipeline: NER-weighted substring matching for recall, rule-based entity discovery for multi-hop expansion, and a CrossEncoder+ColBERT rank fusion stage -- the only learned component -- running on CPU in ~650ms.

## 参考文献

待补充
