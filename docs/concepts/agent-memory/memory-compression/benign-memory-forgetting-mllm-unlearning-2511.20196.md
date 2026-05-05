---
title: "Towards Benign Memory Forgetting for Selective Multimodal Large Language Model Unlearning"
arXiv: 2511.20196
date: 2025-11-25
tags: [agent-memory, memory-compression, privacy]
reviewer: auto
source: arXiv RSS/API
---

# Towards Benign Memory Forgetting for Selective Multimodal Large Language Model Unlearning

## 论文基本信息

- **作者**: Zhen Zeng, Leijiang Gu, Zhangling Duan, Feng Li, Zenglin Shi, Cees G. M. Snoek, Meng Wang
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2511.20196
- **代码**: （待补充）

## 核心贡献

1. **SMFA (Sculpted Memory Forgetting Adapter)**: 提出culpted Memory Forgetting Adapter，将遗忘限制在目标记忆区域同时保留整体能力。
2. **两阶段训练**: 
   - 第一阶段：微调模型将敏感响应替换为拒绝回答，获得记忆遗忘适配器
   - 第二阶段：应用保留锚引导的掩码机制，防止对无关知识和理解能力的干扰
3. **S-MLLMUn Bench**: 首个联合评估敏感知识移除与通用视觉理解保持的基准测试。

## 研究背景与问题

多模态大语言模型（MLLMs）虽然取得了令人瞩目的能力，但可能无意中记忆了隐私敏感信息。现有遗忘方法可以移除这些知识，但往往无法实现良性遗忘——因为它们通常会损害模型的一般图像理解性能。

## 核心方法

**SMFA 包含两个核心组件：**

### 1. 记忆遗忘适配器
微调模型将敏感响应替换为 refusals，获得一个记忆遗忘适配器（adapter）。

### 2. 保留锚引导的掩码机制
在应用遗忘时，通过掩码机制防止对无关知识的干扰：
- **遗忘锚（Forgetting Anchor）**: 引导模型学习如何遗忘
- **保留锚（Retaining Anchor）**: 引导模型保持原有能力

## S-MLLMUn Bench

首个评估选择性 MLLM 遗忘的 benchmark，同时评估：
- 敏感知识的移除程度
- 通用视觉理解能力的保持程度

## 实验结果

大量实验表明，与先前方法不同，SMFA 实现了精确可控的遗忘，同时保持了模型的基础图像理解能力。

## 为什么重要

这是首个系统性研究"选择性遗忘+能力保持"联合优化的 MLLM 工作，对记忆隐私保护有直接意义。在 Agent 系统中，这意味着可以让模型"忘记"某些交互历史而不破坏其整体能力。

## 与移动端/端侧相关性

在端侧部署 MLLM 时，用户隐私数据被模型记忆是重要隐患。SMFA 提供了在边缘设备上实现记忆选择性遗忘的可能路径，同时不牺牲模型能力——这对于手机/手表上的个性化 MLLM 助手尤为重要。
