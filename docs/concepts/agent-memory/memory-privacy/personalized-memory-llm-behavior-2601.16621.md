---
title: "How Does Personalized Memory Shape LLM Behavior? Benchmarking Rational Preference Utilization in Personalized Assistants"
arXiv: 2601.16621
date: 2026-01-23
tags: [agent-memory, memory-privacy]
reviewer: auto
source: arXiv RSS/API
---

# How Does Personalized Memory Shape LLM Behavior? Benchmarking Rational Preference Utilization in Personalized Assistants

**作者:** Xueyang Feng, Weinan Gan, Xu Chen, Quanyu Dai
**发表:** 2026-01-23

## 摘要

LLM 驱动的助手最近集成了记录用户偏好的记忆机制，以提供更个性化和用户对齐的响应。然而，不相关的个性化记忆经常被引入上下文，干扰 LLM 的意图理解。为全面研究个性化的双重效应，本文开发了 RPEval，一个基准测试，包含来自不同领域的现实世界用户偏好数据，用于系统评估个性化记忆对 LLM 行为的影响。

## 核心貢獻

1. **RPEval 基准**: 系统评估个性化记忆对 LLM 行为影响的基准测试
2. **偏好相关性分析**: 发现不相关记忆会显著干扰 LLM 的意图理解
3. **记忆质量评估**: 提供记忆相关性过滤的评估框架，帮助判断哪些记忆真正有价值
4. **双重效应揭示**: 个性化记忆既能提升性能（正确利用偏好），也能降低性能（噪声干扰）
5. **理性偏好利用**: 首次系统研究"理性"偏好利用——何时及如何有效利用用户偏好

## 為什麼重要

这篇论文揭示了个性化记忆的双刃剑效应：它可以提升用户体验，但处理不当反而会损害性能。对于构建实用化个人助手的研究者，这是重要警示——记忆的数量不等于质量，相关性过滤是关键。

## 與端側/移動端相關性

1. **端侧个人助手**: 手机/可穿戴助手是个性化记忆的核心应用场景
2. **隐私敏感**: 端侧记忆存储用户敏感信息，隐私保护是核心
3. **上下文窗口受限**: 移动端上下文窗口更有限，记忆相关性过滤更关键
4. **本地处理**: 个性化评估和过滤应在本地执行，避免上传隐私数据
