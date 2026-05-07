---
title: "GRAVITY: Architecture-Agnostic Structured Anchoring for Long-Horizon Conversational Memory"
arXiv: "2605.01688"
date: "2026-05-03"
tags: [agent-memory, memory-retrieval, structured-memory]
reviewer: auto
source: arXiv API
---

## 论文概述

**核心问题**：现有对话记忆系统在检索后，将记忆片段以**非结构化文本**形式喂给 LLM，缺乏复杂推理所需的**关系、时间、主题结构**。

**解决思路**：GRAVITY（Generation-time Relational Anchoring Via Injected Topological Memory）从对话语料中提取三类结构化知识表示，在生成时以结构化锚定上下文注入宿主模型，无需修改宿主架构。

## 核心贡献

1. **三种结构化知识表示**
   - **Entity Profiles**：基于关系图谱的实体画像
   - **Temporal Event Tuples**：链接为因果链的时间事件元组
   - **Cross-Session Topic Summaries**：跨会话主题摘要

2. **即插即用的模块化设计**：不依赖特定模型架构，可接入任意记忆系统

3. **广泛有效性验证**：在 LongMemEval 和 LoCoMo 两个基准上评测了 5 种不同记忆系统，平均 LLM-Judge 准确率提升 **7.5–10.1%**

## 为什么重要

- 最弱宿主提升 12.2%，最强宿主仍提升 3.8–5.7%——结构化锚定是**普遍有效的增强范式**
- 为长期对话记忆的**结构化推理**提供了新方向

## 与端侧/移动端相关性

1. **架构无关性**：无需修改宿主模型，适合移动端轻量级记忆系统的模块化升级
2. **提示工程而非训练**：不引入额外训练负担，适合资源受限的端侧部署

## 参考链接

- arXiv: https://arxiv.org/abs/2605.01688
