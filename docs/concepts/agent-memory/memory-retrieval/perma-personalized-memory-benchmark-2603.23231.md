---
title: "PERMA: Benchmarking Personalized Memory Agents via Event-Driven Preference and Realistic Task Environments"
arXiv: 2603.23231
date: 2026-03-24
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# PERMA: Benchmarking Personalized Memory Agents via Event-Driven Preference and Realistic Task Environments

**作者:** Shuochen Liu, Junyi Zhu, Long Shu, Junda Lin
**发表:** 2026-03-24

## 摘要

赋予大型语言模型长期记忆对于构建适应用户不断变化需求的 Agent 至关重要。然而，先前的评估通常将偏好相关对话与无关对话交织，将任务简化为"大海捞针"式检索，忽视了驱动用户偏好演变的事件之间的关系。本文提出 PERMA，一种新型基准测试，通过事件驱动偏好和现实任务环境来评估个性化记忆 Agent。

## 核心貢獻

1. **事件驱动的偏好建模**: 超越"大海捞针"检索，关注用户偏好的动态演变过程
2. **PERMA 基准**: 完整的多维度评估框架，涵盖记忆获取、检索、推理和适应能力
3. **事件关系网络**: 将用户事件建模为关系网络，而非扁平记忆条目
4. **现实任务环境**: 提供真实场景下的评估，而非合成对话
5. **偏好推理评估**: 系统评估个性化记忆对下游任务的影响

## 為什麼重要

当前记忆 Agent 评估缺乏统一标准，PERMA 提供了首个系统性基准，对记忆 Agent 的研究和评估有重要推动作用。事件驱动的方法也提示我们：记忆的价值不在于存储多少，而在于能否捕捉和利用事件之间的关系。

## 與端側/移動端相關性

1. **移动端个性化核心**: 手机助手是典型的个性化记忆 Agent，PERMA 的场景直接针对此类应用
2. **低资源评估**: 评估指标设计考虑了端侧部署的计算约束
3. **用户隐私**: 事件驱动的个性化设计需在本地处理用户数据，适合端侧隐私保护
4. **真实场景**: 移动端需要真实环境评估，而非受控实验室
