---
title: "Keys to Knowledge (K2K): Efficient and Effective Internal Memory Retrieval for LLM-Based Healthcare Prediction"
arXiv: "2604.07659"
date: "2026-04-08"
tags: [agent-memory, memory-retrieval, healthcare, internal-memory]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

K2K 针对医疗场景中 LLM 的幻觉和缺乏细粒度医学上下文问题，提出用**内部键值记忆（internal key-based knowledge access）**替代外部检索。

**核心问题**：
- LLM 在高风险临床环境中可靠性不足（幻觉、缺乏细粒度医学上下文）
- 标准 RAG 需要在大规模外部知识库上做计算密集型搜索
- 高延迟在时间敏感的医疗护理场景中不切实际

**K2K 方案**：
- 用内部键值记忆替代外部检索
- 不需要查询外部知识库，通过内部记忆键直接访问相关知识
- 在保持准确率的同时显著降低延迟

## 为什么重要

这是记忆检索在医疗垂直领域的重要应用。内部记忆（internal memory）vs 外部检索（external RAG）的对比研究揭示：对于高频、实时的医疗预测任务，内部记忆访问比外部 RAG 更高效。这对端侧实时推理场景有普遍参考价值。

## 与端侧/移动端的相关性

**高度相关**。医疗是边缘部署的核心场景之一——可穿戴健康监测、院外急救、家庭健康助手都需要低延迟的实时推理。K2K 证明了内部记忆可以在不牺牲准确率的前提下实现超低延迟，对端侧健康 agent 的记忆架构设计有直接指导意义。

## 摘要

Large language models (LLMs) hold significant promise for healthcare, yet their reliability in high-stakes clinical settings is often compromised by hallucinations and a lack of granular medical context. While Retrieval Augmented Generation (RAG) can mitigate these issues, standard supervised pipelines require computationally intensive searches over massive external knowledge bases, leading to high latency that is impractical for time-sensitive care. To address this, we introduce Keys to Knowledge (K2K), a novel framework that replaces external retrieval with internal, key-based knowledge access.

## 参考文献

待补充
