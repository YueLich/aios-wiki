---
title: Fine-Tuning Without Forgetting via Loss-Adaptive Learning Rates
arXiv: 2605.20005
date: 2026-05-19
tags: [agent-memory, continual-learning, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

# Fine-Tuning Without Forgetting via Loss-Adaptive Learning Rates

**arXiv**: 2605.20005 | **日期**: 2026-05-19 | **作者**: Parjanya Prajakta Prashant, Jiongli Zhu, Aldan Creo, Babak Salimi

## 摘要

FINCH 提出了一种新颖的损失自适应学习率调度方法，用于在不抑制高损失 tokens 的前提下控制灾难性遗忘。核心发现：每步遗忘量与学习率和当前训练损失平方根的乘积成正比。据此在高损失批次上降低学习率、在模型收敛时提高学习率，同时保持标准微调目标不变。在知识获取、科学和低资源语言适应基准上，FINCH 平均减少 93% 的遗忘，同时匹配标准微调的任务性能。在 Qwen3-4B 知识获取上，FINCH 将 TruthfulQA 退化减少 5 倍，逆转 HaluEval 退化，并更好地保持置信度校准。

## 核心贡献

1. **（参考文献待从原文补充）**

## 为什么重要

本文针对的是长程 Agent 的记忆系统关键挑战。与传统在离线场景设计的记忆方法不同，本文强调流式/在线视频理解中的实时记忆管理，对端侧 Agent 的实时视觉记忆有重要参考价值。

## 与端侧/移动端的相关性

- 视频流处理对端侧计算资源有严格限制，记忆压缩机制至关重要
- 轻量级视觉记忆管理对移动端/可穿戴设备上的视觉 Agent 有直接应用价值

## 参考文献

（参考文献待从原文补充）
