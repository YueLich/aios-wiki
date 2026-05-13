---
title: "Goal-Mem: Goal-Oriented Reasoning for RAG-based Memory in Conversational Agentic LLM Systems"
arXiv: 2605.12213
date: 2026-05-12
tags: [agent-memory, memory-retrieval, RAG, goal-oriented-reasoning]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Goal-Mem: Goal-Oriented Reasoning for RAG-based Memory in Conversational Agentic LLM Systems
- **arXiv ID**: 2605.12213
- **发表日期**: 2026-05-12
- **作者**: Jiazhou Liang, Armin Toroghi, Yifan Simon Liu
- **方向**: Agent Memory Retrieval / RAG-based Memory
- **类别**: cs.AI

## 摘要

基于 LLM 的对话智能体因有限上下文而在长时域保持一致行为方面存在困难。RAG 方案通过在外部记忆模块存储交互并进行检索来克服这一限制，但其回答挑战性问题（如多跳、常识）的能力最终取决于智能体对检索信息进行推理的能力。

现有方法基于原始用户话语的语义相似度检索记忆，缺乏对缺失中间事实的显式推理，常返回无关或不足以支撑推理的证据。

本文提出 **Goal-Mem**，一个面向 RAG 记忆的目标推理框架，从用户话语作为目标执行显式后向链式推理。Goal-Mem 不是从检索上下文逐步扩展，而是将每个目标分解为原子子目标，执行针对性记忆检索以满足每个子目标，并迭代识别何时需要从记忆检索哪些信息。

论文将这一过程形式化为 **自然语言逻辑（Natural Language Logic）**——一种结合 FOL 可验证性与自然语言表达力的逻辑系统。在两个数据集上与 9 个强记忆基线对比，Goal-Mem 在需要多跳推理和隐式推理的任务上持续提升性能。

## 核心贡献

1. **Goal-Mem 框架**：后向链式目标分解 → 针对性记忆检索 → 迭代子目标解决
2. **自然语言逻辑形式化**：兼容 FOL 验证性与 NL 表达力的推理系统
3. **多跳推理改进**：对需要隐式中间步骤的复杂查询效果显著
4. **通用性**：可叠加于现有 RAG 记忆系统之上

## 为什么重要

RAG 记忆的常见问题是"检索与推理脱节"——只做语义相似度匹配而不理解回答问题真正需要什么。Goal-Mem 引入目标导向推理，让记忆检索真正服务于下游任务。

## 与移动端/端侧相关性

- 端侧对话智能体需要在有限上下文内做高质量记忆检索
- Goal-Mem 的目标分解机制对移动端多跳推理有潜在价值
- 可叠加于轻量 RAG 系统，适合端侧资源受限环境

## 参考文献

- 原文: https://arxiv.org/abs/2605.12213
