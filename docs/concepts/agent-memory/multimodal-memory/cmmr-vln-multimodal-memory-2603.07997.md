---
title: "CMMR-VLN: Continual Multimodal Memory Retrieval for Vision-and-Language Navigation"
arXiv: 2603.07997
date: 2026-03-09
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# CMMR-VLN: Continual Multimodal Memory Retrieval for Vision-and-Language Navigation

## 论文基本信息

- **作者**: Chong Liu, et al.
- **arXiv**: https://arxiv.org/abs/2603.07997
- **领域**: cs.CV, cs.RO

## 摘要

虽然大语言模型被引入视觉-语言导航（VLN）以提升指令理解和泛化，但现有 LLM-based VLN 缺乏选择性回忆和利用相关先前经验来辅助导航任务的能力，限制了在长程和陌生场景中的性能。CMMR-VLN 提出基于持续 multimodal 记忆检索的 VLN 框架，赋予 LLM Agent 结构化记忆和反思能力。CMMR-VLN 构建以全景视觉图像和显著地标索引的 multimodal 经验记忆，在导航时检索相关经验；引入检索增强生成管道，模拟经验人类导航员如何利用先前知识；纳入基于反思的记忆更新策略，选择性地存储成功路径的完整记录和失败案例的关键初始错误。在仿真和真实测试中，成功率分别比 NavGPT、MapGPT 和 DiscussNav 高出 52.9%/20.9%/20.9% 和 200%/50%/50%。

## 核心贡献

1. **Multimodal Experience Memory**: 以全景图像和显著地标索引的 multimodal 经验记忆
2. **Retrieval-augmented Generation Pipeline**: 检索增强生成管道
3. **Reflection-based Memory Update**: 基于反思的选择性记忆更新策略
4. **52.9% Success Rate Improvement**: 仿真测试中显著优于基线
5. **Real-world Deployment**: 真实机器人测试验证

## 研究背景与问题

VLN Agent 需要在长程导航中利用历史经验，但现有方法缺乏结构化记忆机制，无法选择性检索和利用相关经验。

## 核心方法

1. **Panoramic Visual Index**: 以全景图像和地标索引 multimodal 记忆
2. **Retrieval-augmented Navigation**: 检索相关经验辅助导航决策
3. **Selective Memory Update**: 只存储成功路径完整记录和失败案例关键初始错误
4. **LLM Agent Integration**: 与 LLM Agent 无缝集成

## 为什么重要

CMMR-VLN 展示了如何将持续 multimodal 记忆引入具身 Agent 的导航任务。记忆的检索增强和选择性更新策略对其他具身 Agent 有广泛参考价值。

## 与移动端/端侧相关性

1. **具身导航**: 移动机器人、自动驾驶的导航记忆
2. **长程场景**: 支持数十分钟到数小时的长程导航
3. **经验积累**: 移动端可积累跨任务导航经验
4. **真实部署验证**: 真实机器人测试验证了系统可靠性
