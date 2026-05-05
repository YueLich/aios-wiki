---
title: "To Know is to Construct: Schema-Constrained Generation for Agent Memory"
arXiv: 2604.20117
date: 2026-04-22
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# To Know is to Construct: Schema-Constrained Generation for Agent Memory

**作者:** Lei Zheng, Weinan Song, Daili Li, Yanming Yang
**发表:** 2026-04-22

## 摘要

Constructivist epistemology argues that knowledge is actively constructed rather than passively copied. Despite the generative nature of Large Language Models (LLMs), most existing agent memory systems are still based on dense retrieval. However, dense retrieval heavily relies on semantic overlap or entity matching within sentences. Consequently, embeddings often fail to distinguish instances that are semantically similar but contextually distinct, introducing substantial noise by retrieving context-mismatched entries. Conversely, directly employing open-ended generation for memory access risks "Structural Hallucination" where the model generates memory keys that do not exist in the memory, leading to lookup failures. Inspired by this epistemology, we posit that memory is fundamentally organized around schema structures, and propose SCG-MEM: a Schema-Constrained Generation framework for agent memory. SCG-MEM generates memory entries within schema constraints, ensuring structural validity while preserving generative flexibility.

## 核心貢獻

1. **建构主义认识论启发**: 首次将「知识主动建构」的认识论引入 Agent 记忆系统设计
2. **SCG-MEM 框架**: Schema-Constrained Generation，在 schema 约束下生成记忆条目，兼顾结构有效性和生成灵活性
3. **解决密集检索的噪声问题**: 语义相似的上下文可能被误匹配，SCG-MEM 通过 schema 约束避免上下文不匹配的记忆检索
4. **避免结构幻觉**: 开放式生成记忆键时可能产生不存在于记忆中的键，schema 约束确保生成的记忆键有效
5. **记忆的结构化组织**: 记忆围绕 schema 结构组织，支持更精确的记忆检索和推理

## 為什麼重要

现有 Agent 记忆系统大多依赖密集检索，但这在语义相似但上下文不同的实例上表现不佳。SCG-MEM 借鉴建构主义认识论，提出知识不是被动复制而是主动建构的，因此记忆应该围绕 schema 结构组织。这为 Agent 记忆的表示和检索提供了新范式。

## 與端側/移動端相關性

1. **Schema 约束**: 约束生成空间，减少幻觉，提升记忆可靠性
2. **结构化记忆**: 适合移动端知识图谱记忆表示
3. **生成 + 检索混合**: 兼顾生成的灵活性和检索的可靠性
4. **记忆质量提升**: 减少噪声检索和幻觉键，提升端侧记忆系统的可信度
