---
title: "Interactive Episodic Memory with User Feedback"
arXiv: 2604.24893
date: 2026-04-27
tags: [agent-memory, episodic-memory, vision, embodied]
reviewer: auto
source: arXiv RSS/API
---

# Interactive Episodic Memory with User Feedback

## 论文基本信息

- **arXiv ID**: 2604.24893
- **作者**: Nikesh Subedi, Loris Bazzani, Ziad Al-Halah
- **提交日期**: 2026-04-27
- **类别**: cs.CV

## 摘要

在基于自然语言查询的情景记忆（EM-NLQ）中，用户可能提出模糊或不完整的问题（如「我把杯子放哪儿了？」），需要在大段第一人称视角视频中搜索答案。然而现有方法忽视了这一关键问题，在一次性设置中解决 EM-NLQ，限制了实际应用场景。本文提出 EM-QnF（Episodic Memory with Questions and Feedback）任务，用户可以对模型初始预测提供反馈或补充信息（「在此之前，我找的是蓝色大杯子不是白色的」），帮助模型交互式地优化预测。论文收集了基于反馈的交互数据集，并提出轻量级训练方案避免昂贵的序列优化，还引入了即插即用的 Feedback Alignment 模块。

## 核心贡献

1. **EM-QnF 任务定义**：引入带反馈交互的情景记忆查询任务，更贴近真实用户场景。
2. **反馈交互数据集**：包含用户反馈的 EM-NLQ 数据，支持交互式多轮优化。
3. **轻量级训练方案**：避免端到端序列优化的巨大计算开销。
4. **Feedback Alignment 模块**：可插入现有 EM-NLQ 模型的即插即用组件，提升反馈利用效率。

## 为什么重要

现有情景记忆研究假设用户 query 完整且明确，但真实场景中 query 往往模糊、上下文缺失。本文首次系统研究交互式反馈在情景记忆中的作用，将单轮查询扩展为多轮对话优化。这对移动端/端侧 Agent 有直接意义——移动设备上的视觉记忆系统（相册回忆、AR 找物等）本质上就是 EM-NLQ 任务。

## 与移动端/端侧相关性

- 移动端 AR 找物、智能相册回忆等功能本质上是 EM-NLQ 任务
- 用户反馈机制可提升端侧视觉记忆系统的准确率
- 轻量级训练方案适合移动端部署——不需要大规模 GPU 集群
- 多模态记忆（视觉+语言）与移动端传感器融合方向高度相关
