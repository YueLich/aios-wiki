---
title: "Revisiting Catastrophic Forgetting in Continual Knowledge Graph Embedding"
arXiv: 2604.19401
date: 2026-04-21
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Revisiting Catastrophic Forgetting in Continual Knowledge图谱嵌入

## 论文基本信息

- **作者**: Gerard Pons, Carlos Escolano, Besim Bilalli, Anna Queralt
- **arXiv**: https://arxiv.org/abs/2604.19401
- **领域**: cs.LG, cs.AI

## 摘要

知识图谱嵌入（KGE）支持多种下游任务，但实际中知识图谱会随新实体和事实的加入而演化，催生了持续知识图谱嵌入（CKGE）方法。现有 CKGE 方法主要通过限制已有嵌入的改变来处理灾难性遗忘（之前学习任务的性能下降）。但论文证明这一观点不完整。当新实体引入时，其嵌入可能干扰已有嵌入，导致模型在应该是先前正确答案的位置预测新实体。这种"实体干扰"现象在很大程度上被忽视，现有的 CKGE 评估协议也没有考虑。忽视这一效应可能导致性能高估高达 25%。

## 核心贡献

1. **Entity Interference 现象**: 首次识别和系统分析实体干扰问题
2. **Corrected CKGE Evaluation**: 提出考虑实体干扰的修正评估协议
3. **25% Performance Overestimation**: 证明现有方法因忽视实体干扰导致高达 25% 的性能高估
4. **CKGE-specific Forgetting Metric**: 提出针对 CKGE 的遗忘度量
5. **Method × Interference Analysis**: 分析不同 CKGE 方法和 KGE 模型受不同遗忘来源影响的程度

## 研究背景与问题

CKGE 方法主要关注参数（嵌入向量）的改变，但忽视了新实体引入对已有预测的干扰。现有评估只看旧任务的绝对性能，不考虑模型是否开始错误地预测新实体。

## 核心方法

1. **Entity Interference 定义**: 新实体嵌入干扰已有预测的现象
2. **Counterfactual Evaluation**: 反事实评估——如果新实体不存在，模型会怎么预测
3. **Forgetting Metric**: 区分"遗忘已有知识"和"被新实体干扰"两种不同的性能下降
4. **Benchmark Correction**: 在多个基准上应用修正评估协议

## 为什么重要

该研究对 CKGE 领域有重要影响，揭示了当前评估实践的系统性偏差。对基于知识图谱记忆的 Agent 系统，这意味着需要更全面的遗忘评估。

## 与移动端/端侧相关性

1. **端侧知识图谱**: 移动端知识图谱需要持续更新，理解遗忘来源至关重要
2. **实体干扰的现实影响**: 在资源受限设备上，干扰检测可能比完整重训练更高效
3. **知识一致性**: 实体干扰会损害知识图谱记忆的可靠性
