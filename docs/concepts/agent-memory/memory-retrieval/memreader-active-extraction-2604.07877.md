---
title: "MemReader: From Passive to Active Extraction for Long-Term Agent Memory"
arXiv: 2604.07877
date: 2026-04-09
authors: ["Jingyi Kang et al."]
tags: [agent-memory, memory-retrieval, active-extraction, memory-writing, GRPO]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.07877
- **作者**: Jingyi Kang, Chunyu Li, Ding Chen et al.
- **提交日期**: 2026-04-09
- **方向**: 主动记忆提取 / Agent 记忆写入 / 强化学习

## 摘要（全文翻译）

长期记忆是个性化和自主 Agent 的基础，但填充记忆仍是瓶颈。现有系统将记忆提取作为从上下文到结构化条目的单次被动转录，在噪声对话、缺失引用和跨轮依赖上存在困难，导致记忆污染、低价值写入和不一致。

本文引入 **MemReader** 系列用于 Agent 系统中的主动长期记忆提取：MemReader-0.6B，一个紧凑、成本高效的被动提取器，为准确且符合模式的结构化输出而提炼；MemReader-4B，一个用 GRPO（群组相对策略优化）优化的主动提取器，使记忆写入决策具有选择性。在 ReAct 风格范式下，MemReader-4B 显式评估候选记忆的写入价值，有选择地执行写入。

## 核心贡献

1. **主动 vs 被动记忆提取**：MemReader-4B 主动决定是否写入记忆，而非被动转录所有内容
2. **GRPO 优化**：用强化学习（GRPO）让模型学会"什么时候值得写入记忆"
3. **双模型系列**：0.6B 被动提取 + 4B 主动决策，覆盖不同成本-质量权衡
4. **ReAct 风格范式**：在推理过程中评估记忆写入价值

## 为什么重要

现有 Agent 记忆系统的一个根本问题是"什么值得记住"没有明确标准，导致记忆被无差别填充，最终被噪声淹没。MemReader-4B 通过 RL 学会了主动选择——只有真正有价值的交互才写入记忆，从根本上减少了记忆污染。

## 与端侧/移动端的相关性

MemReader 的双模型设计对端侧友好：平时运行轻量的 0.6B 被动提取器，只在必要时调用 4B 主动提取器。这在保持记忆质量的同时控制了端侧的计算成本。
