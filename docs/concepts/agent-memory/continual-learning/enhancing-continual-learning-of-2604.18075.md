---
title: "Enhancing Continual Learning of Vision-Language Models via Dynamic Prefix Weighting"
arXiv: 2604.18075v1
date: 2026-04-20
authors: ["Hyeonseo Jang", "Hyuk Kwon", "Kibok Lee"]
tags: [agent-memory, continual-learning, vision-language-models, prefix-tuning, catastrophic-forgetting]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.18075v1
- **作者**: Hyeonseo Jang, Hyuk Kwon, Kibok Lee
- **提交日期**: 2026-04-20
- **方向**: 持续学习 / VLM / 参数高效微调

## 摘要（全文翻译）

本文研究视觉语言模型（VLM）的领域类增量学习场景。最近的工作使用参数高效方法（如前缀调优或适配器）来应对这一挑战，通过添加性向量将任务特定信息融入输入 token。然而，之前的方法往往对这些向量的权重进行归一化，忽略了不同输入 token 需要不同程度调整的事实。为克服这一问题，本文提出**动态前缀加权（Dynamic Prefix Weighting, DPW）**，一个动态为前缀分配权重并配合适配器的框架。DPW 由两部分组成：1）基于相应输入 token 重要性调整每个前缀权重的门控模块；2）将适配器输出权重推导为前缀调优权重残差的加权机制，确保适配器仅在必要时被使用。在 VLM 领域类增量学习场景中，实验结果证明该方法达到最优性能。

## 核心贡献

1. **动态前缀加权（DPW）机制**：根据输入 token 的重要性动态分配前缀权重，而非统一归一化
2. **门控模块**：评估每个输入 token 的重要性，自适应调整前缀影响程度
3. **残差适配器权重**：将适配器输出作为前缀调优权重的残差，实现两个机制的协同
4. **状态最优的 VLM 增量学习**：在 domain-class 增量学习场景中优于现有方法

## 为什么重要

参数高效方法（prefix-tuning、adapter）是端侧 Agent 在有限存储条件下持续学习的关键技术。但现有方法忽略了一个关键洞察：不同输入 token 对当前任务的重要性不同，统一权重会损害模型区分新旧知识的能力。DPW 通过动态权重分配解决了这一问题，对构建可持续适应新任务同时保留旧知识的端侧记忆系统有直接启发。

## 与端侧/移动端的相关性

**高度相关**。端侧 VLMs（如手机上的多模态模型）需要在有限参数空间内持续学习新领域。DPW 的参数高效特性使其非常适合移动端部署——只存储任务特定的前缀和小型适配器权重，而非完整模型副本，大幅降低存储成本。
