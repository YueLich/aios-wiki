---
title: "MemLens: Benchmarking Multimodal Long-Term Memory in Large Vision-Language Models"
arXiv: 2605.14906
date: 2026-05-14
tags: [agent-memory, memory-retrieval, multimodal-memory, benchmark]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

记忆对于大型视觉-语言模型（LVLMs）处理长时 multimodal 交互至关重要，当前主要有两种方法提供这一能力：长上下文 LVLMs 和记忆增强型 Agents。然而，现有基准测试缺乏对这两种方法在真正需要 multimodal 证据的问题上的系统性比较。MemLens 应运而生，这是一个综合性的 multimodal 多轮对话记忆基准，包含 789 个问题，涵盖五种记忆能力（信息提取、多轮推理、时间推理、知识更新、拒绝回答），在四种标准上下文长度（32K-256K tokens）下采用跨模态 token 计数方案。图像消融研究证实，解决 MemLens 问题确实需要视觉证据：移除证据图像后，两种前沿 LVLMs 在 80.4% 包含图像证据的问题上准确率降至 2% 以下。评估了 27 个 LVLMs 和 7 个记忆增强型 Agents，发现长上下文 LVLMs 通过直接视觉 grounding 在短上下文时达到高准确率，但随对话增长而退化；而记忆型 Agents 在长度上稳定但存储时间压缩下会丢失视觉保真度。多轮推理使大多数系统限制在 30% 以下，两种方法单独都无法解决该任务。这些结果激励了结合长上下文注意力和结构化 multimodal 检索的混合架构。

## 核心贡献

1. **系统性对比范式**：首次对长上下文 LVLMs 和记忆增强型 Agents 在真正需要 multimodal 证据的问题上进行系统性比较。
2. **跨模态 token 计数**：采用标准化的跨模态 token 计数方案，确保评估的公平性。
3. **五种记忆能力的全面覆盖**：信息提取、多轮推理、时间推理、知识更新、拒绝回答。
4. **图像消融验证**：通过消融实验严格证明视觉证据的必要性。
5. **混合架构启示**：揭示了单独使用任一方法的局限性，为结合两种方法的混合架构提供了实证依据。

## 为什么重要

当前评估缺乏对"真正需要 multimodal 证据"问题的测试，很多问题仅靠语言描述就能回答，无法区分"真正保留了视觉细节"和"记住了语言摘要"。MemLens 填补了这一空白，为 multimodal 记忆系统的评估提供了严格的标准。

## 与移动端/端侧的相关性

移动端 multimodal agents 需要处理截图、拍照、屏幕录制等视觉输入，MemLens 的评估维度（视觉保真度、存储压缩、时间稳定性）直接指导端侧 multimodal 记忆模块的设计。对移动端 Agent 的轻量化 multimodal 记忆系统具有重要参考价值。
