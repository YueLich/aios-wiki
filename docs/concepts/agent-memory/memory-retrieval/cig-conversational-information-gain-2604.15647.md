---
title: "CIG: Measuring Conversational信息增益 in Deliberative Dialogues with Semantic Memory Dynamics"
arXiv: 2604.15647
date: 2026-04-17
tags: [agent-memory, memory-retrieval, semantic-memory, dialogue]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **作者**: Ming-Bin Chen, Jey Han Lau, Lea Frermann
- **发表**: 2026-04-17
- **方向**: 记忆检索 · 语义记忆 · 对话评估

## 摘要（翻译）

评估公共 deliberation（审议）的质量不仅需要评估礼貌性或论证结构，还需要评估对话的**信息进展**。本文引入对话信息增益（CIG）框架，从对话如何推进对目标主题的集体理解来评估每个话语。为将 CIG 操作化，本文对一个 evolving semantic memory（演化语义记忆）进行建模：系统从话语中提取原子主张，并将其增量整合为结构化记忆状态。利用该记忆，沿着三个可解释的维度对每个话语进行评分：**新颖性（Novelty）**、**相关性（Relevance）** 和 **隐含范围（Implication Scope）**。

本文在两个经过主持的 deliberation 设置（电视辩论和社区讨论）中标注了 80 个片段，表明记忆驱动的动态（如主张更新次数）比传统启发式方法（如话语长度或 TF-IDF）更能与人类感知到的 CIG 相关。研究团队开发了有效的 LLM-based CIG 预测器，为以信息为中心的对话质量分析铺平了道路。

## 核心贡献

1. **CIG 框架**：提出用语义记忆演化来衡量对话中的信息增益，超越传统的礼貌性/论证结构评估
2. **三维度可解释评分**：Novelty、Relevance、Implication Scope，提供细粒度的信息进展分析
3. **语义记忆动态建模**：将对话过程建模为语义记忆的增量整合过程，为记忆系统的效果评估提供了新思路
4. **LLM-based 预测器**：用大语言模型自动预测 CIG 分数，推动大规模对话质量分析

## 为什么重要

在多智能体协作场景中，理解对话何时真正推进了集体知识而非简单地重复或发散，是衡量 deliberation 质量的核心指标。CIG 框架将语义记忆作为评估的中介，为：
- 多智能体系统的对话质量自动评估
- 记忆系统在对话中的实际效用量化
- deliberative AI 系统的benchmark建立

提供了可操作的评估方法。

## 与移动端/端侧的相关性

在移动端个人助手场景中，理解对话的信息进展有助于：
- 判断是否需要向用户请求更多信息
- 识别用户当前意图的演进方向
- 在嘈杂/碎片化输入中保持记忆的连贯性

---

*注：本文从 nav 条目补全，原文件缺失。*
