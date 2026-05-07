---
title: Memory-QA: Answering Recall Questions Based on Multimodal Memories
arXiv: 2509.18436
date: 2025-09-22
tags: [agent-memory, multimodal-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

# Memory-QA: Answering Recall Questions Based on Multimodal Memories

## 摘要

本文提出 Memory-QA，一个处理基于多模态记忆的召回问答的新任务。该任务涉及根据先前存储的多模态记忆回答回忆问题，包括创建面向任务的记忆、有效利用记忆中的时间和位置信息、以及综合多个记忆回答回忆问题。Memory-QA 提出了一个综合流程 Pensieve，集成了记忆特化的编码、跨模态对齐和情境推理模块。

## 核心贡献

1. **新任务定义**：Memory-QA — 基于多模态记忆的召回问答
2. **Pensieve 流程**：集记忆创建、利用、推理于一体的完整管道
3. **多模态记忆编码**：统一处理视觉、文本、时空信息
4. **时间/位置感知检索**：利用记忆中的时间和位置线索进行精确召回
5. **跨记忆综合**：能够综合多个记忆片段回答复杂问题

## 技术方法

### 任务定义
给定：
- 用户过去体验的多模态记录（视频/图像 + 文本注释）
- 关于这些体验的召回问题（如"我上次去的那个餐厅叫什么？"）

输出：准确回答用户问题

### Pensieve 架构
1. **记忆编码模块**：将多模态输入编码为统一表示
2. **时空对齐模块**：建立不同模态间的时空对应关系
3. **情境推理模块**：基于问题类型选择和组合相关记忆
4. **答案生成模块**：综合记忆内容生成自然语言答案

## 为什么重要

这是首个明确定义"Agent 如何回答关于自身过去经历的问题"的任务。当前 RAG 系统擅长回答关于文档的问题，但无法回答"你记得我上次..."这类关于个人经历的问题。Memory-QA 为构建有真正个人记忆的 Agent 奠定了任务基础。

## 与移动端/端侧相关性

1. **个人助理**：回答"我上次把钥匙放哪了"这类日常回忆问题
2. **健康监测**：根据过去的活动和健康记录回答医疗相关问题
3. **照片回忆**：回答"我去年夏天去了哪些地方"这类视觉记忆问题
4. **隐私保护**：本地多模态记忆处理，避免云端泄露风险

## 参考文献

- Hongda Jiang, Xinyuan Zhang, Siddhant Garg, Rishab Arora. "Memory-QA: Answering Recall Questions Based on Multimodal Memories." arXiv:2509.18436, 2025.
