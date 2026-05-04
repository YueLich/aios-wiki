---
title: "CMMR-VLN: Vision-and-Language Navigation via Continual Multimodal Memory Retrieval"
arXiv: 2603.07997
date: 2026-03-09
tags: [agent-memory, multimodal-memory, embodied-memory, navigation, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **arXiv ID**: 2603.07997v1
- **发表时间**: 2026-03-09
- **方向**: 多模态记忆、具身智能、视觉-语言导航

## 摘要（翻译）

大语言模型（LLM）已被引入视觉-语言导航（VLN）以提升指令理解和泛化能力，但现有基于 LLM 的 VLN 缺乏选择性回忆和利用相关先验经验来完成导航任务的能力，限制了其在长时程和陌生场景中的表现。本文提出 CMMR-VLN（Continual Multimodal Memory Retrieval based VLN），一个为 LLM Agent 赋予结构化记忆和反思能力的 VLN 框架。具体而言，CMMR-VLN 构建了一个以全景视觉图像和显著地标为索引的多模态经验记忆，在导航过程中检索相关经验；引入检索增强生成管道来模拟经验丰富的导航者如何利用先验知识；并结合了基于反思的记忆更新策略，选择性地存储完整的成功路径和失败案例中的关键初始错误。在模拟和真实测试中，综合测试分别展示了平均成功率提升 52.9%、20.9% 和 20.9%，以及 200%、50% 和 50%（相对于 NavGPT、MapGPT 和 DiscussNav）。

## 核心贡献

1. **多模态经验记忆（Multimodal Experience Memory）**：以全景视觉图像和显著地标为索引的多模态记忆结构，支持在 VLN 任务中选择性检索相关先验经验。
2. **检索增强生成管道（Retrieved-Augmented Generation Pipeline）**：模仿人类导航者利用先验知识的机制，使 LLM Agent 在导航过程中能主动检索记忆。
3. **基于反思的记忆更新策略（Reflection-based Memory Update）**：选择性存储成功案例的完整路径，以及失败案例中的关键初始错误，支持持续学习。
4. **显著性能提升**：在模拟和真实测试中，成功率提升 20.9%-200%。

## 为什么重要

CMMR-VLN 解决了 LLM-based VLN 在长时程和陌生场景中的核心瓶颈——缺乏选择性记忆回忆能力。与传统 VLN 依赖即时上下文不同，本文展示了结构化外部记忆如何显著提升 Agent 在复杂导航任务中的表现。其反思性记忆更新策略（分离成功路径与失败初始错误）是一个实用的持续学习设计。

**与移动端/端侧的相关性**：导航是移动端 Agent 的典型场景，端侧设备（如 AR 眼镜、机器人）需要在资源受限条件下实现长时程记忆检索。CMMR-VLN 的全景图像索引策略和选择性存储机制对端侧记忆系统设计有直接参考价值。

## 与本 Wiki 主题的关联

- **多模态记忆**：视觉+语言的多模态经验存储与检索
- **持续学习**：反思性记忆更新策略实现了经验的持续积累
- **记忆的检索与利用**：检索增强生成管道
- **具身记忆**：导航场景下的空间记忆表示
