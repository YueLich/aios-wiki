---
title: "Efficient and Effective Internal Memory Retrieval for LLM-Based Healthcare Prediction"
arXiv: "2604.07659"
date: "2026-04-08"
tags: [agent-memory, memory-retrieval, healthcare, internal-memory]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **内部键值记忆（Internal Key-Value Memory）**：将关键临床信息编码到模型参数空间，用内部键直接访问知识，无需外部知识库查询。
2. **Activation-Guided Probe Construction**：通过激活引导构建探针，提升检索质量。
3. **Cross-Attention Reranking**：交叉注意力重排进一步提升检索精度。
4. **无推理时开销**：在四个医疗预测基准上达到 SOTA，且无推理时额外延迟。

## 方法详解

### 问题背景
医疗场景中 LLM 的幻觉和缺乏细粒度医疗上下文是核心问题。传统 RAG 需要在大规模外部知识库上做密集搜索，延迟高，不适合时间敏感的医疗护理场景。

### K2K 方案
1. **内部记忆替代外部检索**：将关键临床信息编码为键值对，直接存入模型参数。
2. **Key-Based Access**：通过键直接访问对应记忆，无需向量搜索或知识库查询。
3. **激活引导探针**：利用模型激活信号构建高质量检索探针。
4. **交叉注意力重排**：对初步检索结果做交叉注意力驱动的精细重排。

## 为什么重要

这是记忆检索在医疗垂直领域的重要应用。内部记忆（internal memory）vs 外部检索（external RAG）的对比研究揭示：对于高频、实时的医疗预测任务，内部记忆访问比外部 RAG 更高效。这对端侧实时推理场景有普遍参考价值。

## 与端侧/移动端的相关性

**高度相关**。医疗是边缘部署的核心场景之一——可穿戴健康监测、院外急救、家庭健康助手都需要低延迟的实时推理。K2K 证明了内部记忆可以在不牺牲准确率的前提下实现超低延迟，对端侧健康 agent 的记忆架构设计有直接指导意义。

## 摘要

Large language models (LLMs) hold significant promise for healthcare, yet their reliability in high-stakes clinical settings is often compromised by hallucinations and a lack of granular medical context. While Retrieval Augmented Generation (RAG) can mitigate these issues, standard supervised pipelines require computationally intensive searches over massive external knowledge bases, leading to high latency that is impractical for time-sensitive care. To address this, we introduce Keys to Knowledge (K2K), a novel framework that replaces external retrieval with internal, key-based knowledge access. By encoding essential clinical information directly into the model's parameter space, K2K enables rapid retrieval from internal key-value memory without inference-time overhead. We further enhance retrieval quality through activation-guided probe construction and cross-attention reranking. Experimental results demonstrate that K2K achieves state-of-the-art performance across four benchmark healthcare outcome prediction datasets.

## 参考文献

- Mingchen Li, Jiatan Huang, Zonghai Yao, Hong Yu. "Keys to Knowledge (K2K): Efficient and Effective Internal Memory Retrieval for LLM-Based Healthcare Prediction." arXiv:2604.07659, 2026.
