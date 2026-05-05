---
title: "MemReader: From Passive to Active Extraction for Long-Term Agent Memory"
arXiv: 2604.07877
date: 2026-04-09
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# MemReader: From Passive to Active Extraction for Long-Term Agent Memory

**作者:** Jingyi Kang, Chunyu Li, Ding Chen, Bo Tang, Feiyu Xiong
**发表:** 2026-04-09

## 摘要

Long-term memory is fundamental for personalized and autonomous agents, yet populating it remains a bottleneck. Existing systems treat memory extraction as a one-shot, passive transcription from context to structured entries, which struggles with noisy dialogue, missing references, and cross-turn dependencies, leading to memory pollution, low-value writes, and inconsistency. In this paper, we introduce the MemReader family for active long-term memory extraction in agent systems: MemReader-0.6B, a compact and cost-efficient passive extractor distilled for accurate and schema-consistent structured outputs, and MemReader-4B, an active extractor optimized with Group Relative Policy Optimization (GRPO) to make memory writing decisions. Under a ReAct-style paradigm, MemReader-4B explicitly evaluates whether the current interaction contains worth-writing information before writing, reducing unnecessary memory writes while maintaining memory quality.

## 核心貢獻

1. **MemReader Family**: 首个将记忆提取从被动转录转变为主动决策的端到端系统
2. **MemReader-0.6B**: 轻量级被动提取器，蒸馏自大模型，用于准确且 schema 一致的结构化输出
3. **MemReader-4B**: 主动提取器，使用 GRPO 优化记忆写入决策，明确评估当前交互是否包含值得写入的信息
4. **Active Memory Writing**: 在 ReAct 风格范式下，模型显式判断是否写入记忆，减少不必要的记忆污染
5. **降低记忆污染**: 通过主动决策机制过滤低价值写入，保持记忆质量

## 為什麼重要

现有 Agent 记忆系统将记忆提取视为一次性被动转录，这导致噪声对话、缺失引用和跨轮依赖问题，使记忆充满污染和低价值写入。MemReader 首次将记忆写入从被动转录转变为主动决策——模型主动评估当前交互是否值得记忆。这对 Agent 记忆系统的长期质量控制有根本性贡献。

## 與端側/移動端相關性

1. **轻量级模型 (0.6B/4B)**: 蒸馏后的模型适合端侧部署
2. **主动写入决策**: 减少不必要的 API 调用和存储写入，降低带宽和存储消耗
3. **GRPO 优化**: 强化学习驱动的写入策略可在端侧资源约束下高效运行
4. **记忆质量控制**: 对移动端个人助理的记忆管理有直接参考价值
