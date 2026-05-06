---
title: "SmartSearch: How Ranking Beats Structure for Conversational Memory Retrieval"
arXiv: "2603.15599"
date: "2026-03-16"
tags: [agent-memory, memory-retrieval, conversational-memory, ranking]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **全确定性检索管道**：完全摒弃 LLM-based 结构化和 learned retrieval policies，仅使用 NER 加权子串匹配 + 规则化实体发现 + CrossEncoder+ColBERT rank fusion。
2. **CPU 友好**：整个 pipeline 在 CPU 上运行，延迟 ~650ms，不依赖 GPU。
3. **编译瓶颈分析**：通过 Oracle 分析揭示了记忆检索的真正瓶颈不在召回（98.6% 召回率），而在编译（compilation）——即如何将召回的证据压缩到 token budget 内。
4. **Score-Adaptive Truncation**：根据分数自适应截断，而非固定长度截断，在 LoCoMo 上达到 93.5%，在 LongMemEval-S 上达到 88.4%。

## 方法详解

### 检索管道
1. **NER-Weighted Substring Matching**：对对话历史进行命名实体识别，实体词加权后做子串匹配，保证高召回。
2. **Rule-Based Entity Discovery**：用规则发现多跳实体关系，支撑多跳查询。
3. **CrossEncoder + ColBERT Rank Fusion**：两种排序方法的融合，是唯一的 learned component。
4. **Score-Adaptive Truncation**：根据检索分数动态决定截断位置，确保最重要的证据不被截断。

## 为什么重要

这篇论文是对"复杂即更好"范式的根本性挑战。在 memory retrieval 领域，学术界倾向于设计越来越复杂的架构，但 SmartSearch 证明简单、确定性的方法配合高效排序即可超越复杂的 LLM-based 结构化和 learned retrieval policies。

## 与端侧/移动端的相关性

**高度相关**。SmartSearch 的 pipeline 完全在 CPU 上运行（~650ms），不依赖 GPU。这对移动端部署极其友好——无需昂贵 GPU 即可部署高质量对话记忆检索系统。

## 摘要

Recent conversational memory systems invest heavily in LLM-based structuring at ingestion time and learned retrieval policies at query time. We show that neither is necessary. SmartSearch retrieves from raw, unstructured conversation history using a fully deterministic pipeline: NER-weighted substring matching for recall, rule-based entity discovery for multi-hop expansion, and a CrossEncoder+ColBERT rank fusion stage -- the only learned component -- running on CPU in ~650ms. Oracle analysis on two benchmarks identifies a compilation bottleneck: retrieval recall reaches 98.6%, but without intelligent ranking only 22.5% of gold evidence survives truncation to the token budget. With score-adaptive truncation and no per-dataset tuning, SmartSearch achieves 93.5% on LoCoMo and 88.4% on LongMemEval-S, exceeding all known memory systems under the same evaluation protocol on both benchmarks while using 8.5x fewer tokens than full-context baselines.

## 参考文献

- Jesper Derehag, Carlos Calva, Timmy Ghiurau. "SmartSearch: How Ranking Beats Structure for Conversational Memory Retrieval." arXiv:2603.15599, 2026.
