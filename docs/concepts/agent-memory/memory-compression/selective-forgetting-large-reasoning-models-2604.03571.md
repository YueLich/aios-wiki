---
title: "Selective Forgetting for Large Reasoning Models"
arXiv: 2604.03571
date: 2026-04-04
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Selective Forgetting for Large Reasoning Models

## 论文基本信息

- **作者**: Yuxiang Wei, Zhenting Wang, Kai Mei, Qi Pang, Shuai Zhang, Haizhou Zheng
- **arXiv**: https://arxiv.org/abs/2604.03571
- **领域**: cs.AI, cs.LG

## 摘要

大语言模型在推理过程中会积累大量中间推理状态，当上下文超出限制时需要选择性遗忘。Selective Forgetting 研究如何在不损害核心推理能力的前提下，有策略地遗忘不再需要的推理中间状态。该方法区分"有价值的推理链"和"临时的中间假设"，只遗忘后者。在数学推理、代码生成等需要长链推理的任务上，该方法在不损失最终答案准确率的情况下，将有效上下文窗口利用率提升 40%。

## 核心贡献

1. **Selective Forgetting 框架**: 系统性地研究大推理模型的选择性遗忘问题
2. **Value-aware Forgetter**: 训练一个价值评估器，判断每个中间状态的后续利用价值
3. **40% Context 利用率提升**: 在保持准确率的同时显著提升有效上下文利用率
4. **无损推理**: 遗忘策略确保关键推理链被保留，只清除临时假设
5. **通用设计**: 可与任何链式推理方法结合，不限于特定模型架构

## 研究背景与问题

LLM 推理过程中会生成大量中间步骤（CoT、代码执行结果等），这些中间状态占用大量上下文，但并非都有价值。传统的全部保留或全部丢弃都不可取——需要选择性遗忘那些"后续不会再用"的状态。

## 核心方法

1. **Reasoning State Graph**: 将推理过程建模为状态图，节点=推理步骤，边=依赖关系
2. **Value Estimator**: 训练一个轻量级网络评估每个状态节点的后续利用价值
3. **Forgetter Policy**: 基于价值评估决定保留/遗忘/压缩每个状态节点
4. **Backward Pruning**: 从最终答案反向追溯，只保留对最终答案有贡献的状态
5. **Forward Compression**: 对被标记为"临时的"状态进行有损压缩（如只保留关键变量绑定）

## 为什么重要

选择性遗忘是解决 Agent 记忆资源有限性的重要技术。该论文首次系统定义了"推理状态价值"的概念和评估方法，为记忆压缩提供了更精细化的方向——不是粗粒度地全部压缩或全部保留，而是根据实际价值区分对待。

## 与移动端/端侧相关性

1. **上下文窗口利用率**: 40% 提升意味着在同等硬件条件下可处理更长的推理任务
2. **轻量级 Value Estimator**: 小型网络可在端侧运行，不依赖云端
3. **实时推理优化**: 对手机实时语音助手、车载对话系统等有直接价值
4. **增量式遗忘**: 可在推理过程中逐步遗忘，不需要预先知道全部上下文
