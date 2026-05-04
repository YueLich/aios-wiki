---
title: "CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics"
arXiv: 2604.15647
date: 2026-04-17
tags: [agent-memory, semantic-memory, dialogue, information-gain, deliberation]
reviewer: auto
source: arXiv RSS/API
---

# CIG: Measuring Conversational Information Gain in Deliberative Dialogues with Semantic Memory Dynamics

## 论文基本信息

- **arXiv ID**: 2604.15647
- **作者**: (From paper)
- **提交日期**: 2026-04-17
- **类别**: cs.CL, cs.AI

## 摘要

Measuring the quality of public deliberation requires evaluating not only civility or argument structure, but also the informational progress of a conversation. We introduce a framework for Conversational Information Gain (CIG) that evaluates each utterance in terms of how it advances collective understanding of the target topic. To operationalize CIG, we model an evolving semantic memory of the discussion: the system extracts atomic claims from utterances and incrementally consolidates them into a structured memory state. Using this memory, we score each utterance along three interpretable dimensions: Novelty, Relevance, and Implication Scope. We annotate 80 segments from two moderated deliberative settings (TV debates and community discussions) with these dimensions and show that memory-derived dynamics correlate more strongly with human-perceived CIG than traditional heuristics such as utterance length or TF-IDF.

## 核心贡献

1. **对话信息增益（CIG）框架**：评估每次发言如何推进对目标话题的集体理解。
2. **演化语义记忆模型**：将对话中的原子声明提取并增量整合为结构化记忆状态。
3. **三维可解释评分**：新颖性（Novelty）、相关性（Relevance）和含义范围（Implication Scope）。
4. **超越传统启发式**：记忆衍生动态比传统方法（发言长度、TF-IDF）与人类感知 CIG 的相关性更强。

## 为什么重要

公共讨论质量评估长期以来只关注礼貌性或论点结构，而忽视了信息进步。CIG 框架通过语义记忆动态为对话质量评估提供了新视角，证明了记忆演化与人类感知的信息增益密切相关。这对评估 AI 参与的多方讨论系统（如调解 Agent、辩论助手）有直接价值。

## 与移动端/端侧相关性

- 移动端 AI 助手参与多方讨论时需要评估对话中的信息价值
- 语义记忆框架可应用于移动端会议摘要、多方聊天记录分析
- 三维评分（新颖性/相关性/含义范围）适合在资源受限的端侧环境实现
- 对话质量自动评估对移动端 AI 助手产品化（如智能邮件摘要、群聊总结）有直接价值
