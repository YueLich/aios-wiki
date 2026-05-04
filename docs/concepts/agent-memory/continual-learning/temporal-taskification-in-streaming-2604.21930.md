---
title: "Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability"
arXiv: 2604.21930
date: 2026-04-23
authors: ["Nicolae Filat", "Ahmed Hussain", "Konstantinos Kalogiannis"]
tags: [agent-memory, continual-learning, streaming-CL, evaluation-benchmark, instability]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.21930
- **作者**: Nicolae Filat, Ahmed Hussain, Konstantinos Kalogiannis
- **提交日期**: 2026-04-23
- **方向**: 流式持续学习 / 评估稳定性 / 基准测试

## 摘要（全文翻译）

流式持续学习（CL）通常通过时间划分将连续流转换为离散任务序列。本文认为，这种时间任务化步骤不是中性的预处理选择，而是一个**结构性评估组件**：同一数据流的不同有效划分可以导致不同的 CL 机制，从而导致不同的基准测试结论。

## 核心贡献

1. **时间任务化作为评估变量**：揭示了任务划分方式对 CL 基准结论的巨大影响
2. **评估不稳定性的来源**：同一个数据流，不同任务划分，得出不同"最优方法"
3. **稳健 CL 评估的指导**：如何设计更稳定的流式 CL 基准

## 为什么重要

这提醒 CL 研究者：流式 CL 的评估结论可能对数据划分方式敏感，导致研究结论不可复现或被过拟合。基准测试需要更鲁棒的任务划分策略。
