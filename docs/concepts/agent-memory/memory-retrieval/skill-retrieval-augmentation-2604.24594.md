---
title: "Skill Retrieval Augmentation for Agentic AI"
arXiv: "2604.24594"
date: "2026-04-27"
tags: [agent-memory, memory-retrieval, skill-retrieval, agentic-ai]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **作者**: Weihang Su, Jianming Long, Qingyao Ai
- **方向**: 技能检索、Agentic AI
- **应用**: LLM Agent 工具调用、任务规划

## 研究背景与问题

随着 LLM 进化为智能体问题求解器，它们越来越依赖外部可复用的技能来处理超出参数能力范围的任务。现有 Agent 系统中，主流策略是将可用技能枚举在上下文窗口中。但这一策略在技能语料库扩大时失效：上下文预算被迅速消耗，Agent 在识别正确技能方面的准确性显著下降。

## 核心方法

本文提出了技能检索增强方法：

1. **外部技能库**：将技能从上下文窗口外部化到可检索的知识库
2. **动态技能检索**：根据任务需求动态从技能库中检索相关技能
3. **可扩展架构**：打破上下文长度限制，支持大规模技能管理

## 核心贡献

1. **解决上下文长度限制问题**：通过外部检索而非枚举的方式管理技能
2. **提升技能选择准确性**：在技能库规模扩大时仍保持高准确性
3. **通用可扩展框架**：适用于各类 Agentic AI 系统

## 为什么重要

随着 Agent 系统变得越来越复杂，技能数量持续增长。Skill Retrieval Augmentation 直接解决了上下文窗口的扩展性瓶颈，是构建大规模 Agent 系统的关键技术。

## 与端侧/移动端的相关性

端侧 Agent 往往受限于计算资源和上下文长度。外部技能检索架构使得端侧 Agent 能够在有限资源下访问大规模技能库，对移动端智能助手具有重要价值。

## 参考文献

- 原文: [arXiv:2604.24594](https://arxiv.org/abs/2604.24594)
