---
title: "Mem-Gallery: Benchmarking Multimodal Long-Term Conversational Memory for MLLM Agents"
arXiv: "2601.03515"
date: "2026-01-07"
tags: [agent-memory, multimodal-memory, benchmark, long-term-memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **作者**: Yuanchen Bei, Tianxin Wei, Xuying Ning
- **方向**: 多模态长期对话记忆基准测试
- **应用**: MLLM Agent 评估、对话系统

## 研究背景与问题

长期记忆是多模态大语言模型（MLLM）Agent 的关键能力，尤其在信息积累和演化的对话场景中。然而现有基准要么仅评估文本多会话记忆，要么在局部上下文中评估多模态理解，无法评估多模态记忆如何在长期对话轨迹中被保留、组织和演化。

## 核心方法：Mem-Gallery

Mem-Gallery 提出了首个多模态长期对话记忆基准：

1. **多会话多模态评估**：覆盖文本、图像、视频等多种模态的长期记忆保持
2. **对话轨迹建模**：评估信息如何在多轮对话中积累和演化
3. **多维度评估指标**：记忆的准确性、相关性、完整性等多维度评估

## 核心贡献

1. **首个多模态长期对话记忆基准**：填补了该领域的评估空白
2. **全面的评估维度**：覆盖保留、组织、演化三个记忆核心维度
3. **推动 MLLM Agent 记忆研究**：为多模态记忆系统的研发提供标准化评估

## 为什么重要

多模态 Agent 在现实应用中需要处理跨时间、多模态的复杂对话。Mem-Gallery 为该领域提供了首个系统性评估框架，将极大推动多模态长期记忆技术的发展。

## 与端侧/移动端的相关性

移动端智能助手需要长期记住用户的偏好和对话历史。Mem-Gallery 的评估框架可直接用于指导端侧多模态记忆系统的设计与优化。

## 参考文献

- 原文: [arXiv:2601.03515](https://arxiv.org/abs/2601.03515)
