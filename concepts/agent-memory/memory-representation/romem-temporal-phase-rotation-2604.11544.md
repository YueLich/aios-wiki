---
title: "Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory"
arXiv: 2604.11544
date: 2026-04-13
tags: [agent-memory, memory-representation, temporal-knowledge-graph, knowledge-memory]
reviewer: auto
source: arXiv RSS/API
---

# Time is Not a Label: Continuous Phase Rotation for Temporal Knowledge Graphs and Agentic Memory

## 论文基本信息

- **arXiv ID**: 2604.11544
- **作者**: (From paper)
- **提交日期**: 2026-04-13
- **类别**: cs.AI, cs.CL

## 摘要

Structured memory representations such as knowledge graphs are central to autonomous agents and other long-lived systems. However, most existing approaches model time as discrete metadata, either sorting by recency (burying old-yet-permanent knowledge), simply overwriting outdated facts, or requiring an expensive LLM call at every ingestion step, leaving them unable to distinguish persistent facts from evolving ones. To address this, we introduce RoMem, a drop-in temporal knowledge graph module for structured memory systems, applicable to agentic memory and beyond. A pretrained Semantic Speed Gate maps each relation's text embedding to a volatility score, learning from data that evolving relations (e.g., "president of") should rotate fast while persistent ones (e.g., "born in") should remain stable. Combined with continuous phase rotation, this enables geometric shadowing: obsolete facts are rotated out of phase in complex vector space, so temporally correct facts naturally outrank contradictions without deletion. On temporal knowledge graph completion, RoMem achieves state-of-the-art results on ICEWS05-15 (72.6 MRR). Applied to agentic memory, it delivers 2-3x MRR and answer accuracy on temporal reasoning (MultiTQ), dominates hybrid benchmark (LoCoMo), preserves static memory with zero degradation (DMR-MSC), and generalises zero-shot to unseen financial domains (FinTMMBench).

## 核心贡献

1. **RoMem 时序知识图谱模块**：将时间建模为连续相位旋转，而非离散元标签。
2. **语义速度门预训练**：为每个关系学习波动性分数，区分快速旋转关系（如「总统」）和稳定关系（如「出生于」）。
3. **几何遮蔽机制**：通过相位旋转让过时事实在复向量空间中自然被遮蔽，无需删除即可实现时序正确性。
4. **零样本泛化能力**：泛化到未见过的金融领域（FinTMMBench）。

## 为什么重要

时间一直是知识图谱和 Agent 记忆系统中的难题——大多数方法将时间建模为离散元标签，导致：(1) 按时效排序会将「虽旧但永久」的知识埋没；(2) 直接覆盖过时事实会丢失历史；(3) 每次摄取都调用 LLM 成本高昂。RoMem 通过连续相位旋转优雅地解决了这些问题，在时序知识图谱补全（ICEWS05-15: 72.6 MRR）和 Agent 记忆时序推理（MultiTQ: 2-3x MRR）上均达到 SOTA。

## 与移动端/端侧相关性

- 移动端 Agent 需要追踪用户的时序信息（日程、位置历史、对话上下文）
- 无需删除的遮蔽机制适合隐私场景——某些历史事实被「遗忘」但技术上未物理删除
- 零样本泛化对资源受限的端侧很重要——不需要为每个用户域微调
- 2-3x MRR 提升意味着更少检索开销，对移动端低功耗需求友好
