---
title: "GAM: Hierarchical Graph-based Agentic Memory for LLM Agents"
arXiv: 2604.12285
date: 2026-04-14
tags: [agent-memory, memory-representation, knowledge-graph]
reviewer: auto
source: arXiv RSS/API
---

# GAM: Hierarchical Graph-based Agentic Memory for LLM Agents

## 论文基本信息

- **arXiv ID**: 2604.12285
- **作者**: Zhaofen Wu, Hanrong Zhang, Fulin Lin, Wujiang Xu, Xinran Xu
- **提交日期**: 2026-04-14
- **类别**: cs.AI

## 摘要

为维持连贯的长期交互，LLM Agent 必须在获取新信息和保留先前知识之间取得平衡。当前的统一流式记忆系统虽便于上下文更新，但易受瞬态噪声干扰；离散的结构化记忆架构虽能保持知识稳固性，但对演化叙事的适应能力不足。本文提出 GAM（Graph-based Agentic Memory），一种分层图结构记忆框架，将记忆编码与整合显式解耦以解决快速上下文感知与稳定知识保留之间的冲突。通过将对话隔离在事件进展图中，仅在语义转换时整合到主题关联网络，最小化干扰同时保持长期一致性。此外，GAM 引入图引导多因素检索策略增强上下文预测。

## 核心贡献

1. **分层图结构**：事件进展图（对话内）+ 主题关联网络（跨对话），显式分离短期与长期记忆。
2. **记忆编码与整合解耦**：编码阶段隔离新信息，仅在语义转换时执行整合，避免噪声干扰。
3. **图引导多因素检索**：利用图结构指导检索，综合多种相关因素提升精度。
4. **实验验证**：在长程交互任务上验证了 GAM 相比统一流式记忆的优势。

## 为什么重要

GAM 解决了 Agent 记忆系统中「灵活性 vs 稳定性」的核心矛盾——既要能快速吸收新信息，又不能被噪声干扰破坏长期知识结构。分层图结构提供了一种介于纯流式（灵活但脆弱）和纯模块化（稳定但僵化）之间的中间路线。对移动端/端侧 Agent 的启示：移动端 App 交互模式相对固定，图结构记忆可以捕捉 App 间的语义关系，支持跨 App 任务执行。

## 与移动端/端侧相关性

- 移动端多 App 协作场景（如日历 + 邮件 + 导航）与 GAM 的分层图结构高度契合
- 主题关联网络可建模用户习惯的 App 使用模式，支持意图预测
- 图引导检索相比向量检索更可解释，适合隐私敏感场景
