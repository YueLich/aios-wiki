---
title: "CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics"
arXiv: 2604.15647
date: 2026-04-17
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics

**作者:** Ming-Bin Chen, Jey Han Lau, Lea Frermann
**发表:** 2026-04-17

## 摘要

Measuring the quality of public deliberation requires evaluating not only civility or argument structure, but also the informational progress of a conversation. We introduce a framework for Conversational Information Gain (CIG) that evaluates each utterance in terms of how it advances collective understanding of the target topic. To operationalize CIG, we model an evolving semantic memory of the discussion: the system extracts atomic claims from utterances and incrementally consolidates them into a structured memory state. Using this memory, we score each utterance along three interpretable dimensions: Novelty, Relevance, and Implication Scope. We annotate 80 segments from two moderated deliberative settings (TV debates and community discussions) with these dimensions and show that memory-derived dynamics (e.g., the number of claim updates) correlate more strongly with human-perceived CIG than traditional heuristics such as utterance length or TF-IDF. We develop effective LLM-based CIG predictors paving the way for information-focused conversation quality analysis in dialogues and deliberative success.

## 核心贡献

1. **CIG 框架**: 提出对话信息增益（Conversational Information Gain）评估框架，衡量每轮发言对集体理解的推进程度
2. **语义记忆动态建模**: 系统从每轮发言中提取原子主张（atomic claims），逐步整合为结构化记忆状态
3. **三维度评分**: Novelty（新奇性）、Relevance（相关性）、Implication Scope（隐含范围）
4. **实验验证**: 在 TV 辩论和社区讨论的 80 个片段上，记忆动态指标比传统启发式方法与人类判断的相关性更强
5. **LLM-based CIG 预测器**: 为信息聚焦的对话质量分析铺平道路

## 为什么重要

现有对话质量评估主要关注礼貌性或论证结构，忽略了信息增量。CIG 首次提出从语义记忆动态角度评估对话信息增益，并证明记忆演化指标比传统文本特征更能预测人类感知的对话质量。这一框架对 Agent 记忆系统的「记忆价值评估」和「什么时候该记住」具有直接的理论和方法论贡献。

## 与端侧/移动端相关性

1. **增量式记忆更新**: 每轮发言后只更新新出现的 claims，适合端侧增量学习范式
2. **原子主张提取（Atomic Claims）**: 轻量级语义单元，比完整对话历史更节省存储
3. **三维度评分（Novelty/Relevance/Scope）**: 可作为端侧记忆优先级排序的参考指标——决定哪些信息值得记忆
4. **LLM-based 预测器**: 训练后可用于端侧推理，无需每次都调用大模型
