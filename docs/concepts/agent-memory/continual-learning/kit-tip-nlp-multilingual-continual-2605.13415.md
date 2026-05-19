---
title: "KIT-TIP-NLP at MultiPride: Continual Learning with Multilingual Foundation Model"
arXiv: 2605.13415
date: 2026-05-13
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文提出了一个多阶段框架，用于在多语言社交媒体话语中检测被 reclaim 的 LGBTQ+ 相关 slurs。研究解决了识别 reclamatory 与非 reclamatory 用法之间的挑战，同时处理数据稀缺、类别不平衡和跨语言情感表达差异三大方法论难题。框架整合了交叉验证驱动的数据驱动模型选择、通过回译的语义保持增强、带有动态 epoch 级欠采样的归纳迁移学习，以及通过掩码语言建模注入的领域特定知识。

## 核心贡献

1. **多语言 slur 检测的持续学习框架**：首次将持续学习应用于多语言 reclaimed slur 检测任务
2. **三重挑战的系统解决**：同时处理数据稀缺、类别不平衡和跨语言变异性
3. **多语言嵌入模型系统评估**：对 8 种多语言嵌入模型进行系统评估，选择 XLM-RoBERTa 作为基础模型
4. **动态 epoch 级欠采样**：提出新的采样策略以平衡新旧任务知识

## 为什么重要

在端侧 Agent 的实际部署中，模型需要持续适应新的语言现象和文化相关的语义变化。该研究展示了如何用持续学习框架处理多语言环境下敏感内容的动态识别，对移动端的内容审核 Agent 有直接价值。

## 与移动端/端侧的相关性

移动端的内容审核 Agent 需要在资源受限条件下持续学习新词汇和新的语言表达。XLM-RoBERTa 的轻量级变体可以部署在端侧，持续学习框架使模型能够增量适应新的 slang 和语言现象而不需要完整重训练。
