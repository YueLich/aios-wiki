---
title: "Human-Inspired Context-Selective Multimodal Memory for Social Robots"
arXiv: 2604.12081
date: 2026-04-13
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# Human-Inspired Context-Selective Multimodal Memory for Social Robots

## 论文基本信息

- **作者**: Hangyeol Kang, Slava Voloshynovskiy, Nadia Magnenat Thalmann
- **arXiv**: https://arxiv.org/abs/2604.12081
- **领域**: cs.RO, cs.AI

## 摘要

记忆对社会互动至关重要，使人类能够回忆有意义的历史经历并据此调整行为。然而，大多数当前社交机器人和具身 Agent 依赖非选择性的纯文本记忆，限制了个性化、上下文感知互动的能力。论文提出一种受认知神经科学启发的上下文选择性 multimodal 记忆架构，捕捉和检索文本和视觉情景痕迹，优先处理高情感显著性或场景新颖性时刻。通过将这些记忆与个体用户关联，系统实现社交个性化回忆和更自然、更接地气的对话。在社交场景数据集上评估选择性存储机制，达到 0.506 的 Spearman 相关性，超越人类一致性（ρ=0.415），优于现有图像记忆模型。multimodal 检索实验中，融合方法将 Recall@1 提升至多模态文本或图像检索的 13% 以上。运行时评估确认系统保持实时性能。

## 核心贡献

1. **Context-selective Multimodal Memory**: 受神经科学启发的选择性 multimodal 记忆架构
2. **Emotional/Novalty Prioritization**: 优先存储高情感显著性或场景新颖性时刻
3. **Social Personalization**: 通过用户关联实现个性化回忆
4. **Spearman 0.506**: 超过人类一致性（ρ=0.415）的选择性评估
5. **13% Recall@1 提升**: multimodal 检索融合方法显著优于单模态

## 研究背景与问题

现有社交机器人记忆缺乏选择性——同等对待所有交互，无法优先处理重要时刻。认知神经科学表明人类记忆有自然的选择性（情感、新颖性优先）。

## 核心方法

1. **Saliency-based Selection**: 基于情感显著性和场景新颖性的记忆选择
2. **Multimodal Episodic Traces**: 文本和视觉情景记忆的统一表示
3. **User-associated Memory**: 将记忆与个体用户关联
4. **Fusion Retrieval**: 融合文本和视觉检索结果
5. **Real-time Performance**: 保持实时性能的算法设计

## 为什么重要

该研究将认知科学的选择性记忆机制引入社交机器人 multimodal 记忆系统，对需要长程个性化交互的 Agent 有重要参考价值。

## 与移动端/端侧相关性

1. **社交机器人**: 移动端/家庭机器人的核心应用场景
2. **实时性**: 保持实时性能，适合移动端部署
3. **个性化**: 用户关联记忆支持移动端个性化服务
4. **隐私保护**: 用户特定记忆可在本地存储
