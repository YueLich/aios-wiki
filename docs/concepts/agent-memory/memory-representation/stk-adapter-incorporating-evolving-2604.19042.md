---
title: "STK-Adapter: Incorporating Evolving Graph and Event Chain for Temporal Knowledge Graph Extrapolation"
arXiv: 2604.19042v1
date: 2026-04-21
authors: ["Shuyuan Zha", "Yujie Wang", "Zhichun Wang", "Jizhou Guo", "Yong Liu", "Haibin Wan"]
tags: [agent-memory, memory-representation, temporal-knowledge-graph, LLM, event-chain]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.19042v1
- **作者**: Shuyuan Zha, Yujie Wang, Zhichun Wang, Jizhou Guo, Yong Liu, Haibin Wan
- **提交日期**: 2026-04-21
- **方向**: 时序知识图谱 / LLM / 事件推理

## 摘要（全文翻译）

时序知识图谱（TKG）外推旨在基于历史事实预测未来事件。最近的研究试图将 TKG 的演化结构表示和文本事件链整合到大语言模型（LLM）中以增强 TKG 外推。然而，两个主要挑战限制了这些方法：1）TKG 演化结构表示与 LLM 语义空间之间的浅层对齐导致关键时空信息丢失；2）在 LLM 微调过程中 TKG 演化结构特征逐渐稀释。本文提出**时空知识适配器（STK-Adapter）**，灵活整合演化图编码器与 LLM 以促进 TKG 推理。STK-Adapter 设计了时空混合专家（MoE）来捕捉 TKG 固有的空间结构和时间模式；事件感知 MoE 建模事件链内复杂的时间语义依赖；跨模态对齐 MoE 通过 TKG 引导的注意力专家促进深度跨模态对齐。在基准数据集上的实验表明，STK-Adapter 显著优于最优方法，并展现出强大的跨数据集泛化能力。

## 核心贡献

1. **时空 MoE（ST-MoE）**：捕捉 TKG 的空间结构和时间模式
2. **事件感知 MoE（EA-MoE）**：建模事件链内复杂的时间语义依赖
3. **跨模态对齐 MoE（CMA-MoE）**：实现 TKG 结构与 LLM 语义的深度对齐
4. **跨数据集强泛化能力**：实验证明在不同数据集间迁移效果良好

## 为什么重要

Agent 需要基于历史事件序列进行推理和规划。TKG 提供了一种结构化表示事件时间关系的方式，而 LLM 提供了语义理解能力。STK-Adapter 的核心贡献是解决了两者结合时的信息损失问题——TKG 的结构化时空信息在微调过程中被稀释。这对构建具有时间感知能力的 Agent 记忆系统至关重要：Agent 不仅需要记住"发生了什么"，还需要理解"事件的时间顺序如何影响未来决策"。

## 与端侧/移动端的相关性

**中等相关**。TKG + LLM 的组合在端侧部署面临显著挑战——TKG 的图结构存储和时空推理都需要大量计算。但 STK-Adapter 的模态对齐方法对端侧有启发：移动端 Agent 需要将结构化事件日志与语义理解有效融合，而非简单地将图结构作为额外文本输入。
