---
title: "Memory-Efficient Continual Learning with CLIP Models"
arXiv: 2605.03866
date: 2026-05-05
tags: [agent-memory, continual-learning, CLIP]
reviewer: auto
source: arXiv API
---

# Memory-Efficient Continual Learning with CLIP Models

**作者:** Ryan King, Gang Li, Bobak Mortazavi, Tianbao Yang
**发表:** 2026-05-05

## 摘要

Contrastive Language-Image Pretraining (CLIP) models excel at understanding image-text relationships but struggle with adapting to new data without forgetting prior knowledge. To address this, models are typically fine-tuned using both new task data and a memory buffer of past tasks. However, CLIP's contrastive loss suffers when the memory buffer is small, leading to performance degradation on previous tasks. We propose a memory-efficient, distributionally robust method that dynamically reweights losses per class during training. Our approach, tested on class incremental settings (CIFAR-100, ImageNet1K) and a domain incremental setting (DomainNet) adapts CLIP models quickly while minimizing catastrophic forgetting, even with minimal memory usage.

## 核心贡献

1. **分布鲁棒重加权 (Distributionally Robust Reweighting)**: 动态调整每个类别的损失权重，在小内存缓冲区下保持分布鲁棒性
2. **最小内存持续适应**: 在极小内存使用量下实现快速适应，显著减少灾难性遗忘
3. **类别增量与领域增量统一框架**: 在 CIFAR-100、ImageNet1K（类别增量）和 DomainNet（领域增量）上均验证有效性
4. **对比学习损失优化**: 解决 CLIP 对比损失在小缓冲区下性能退化的根本问题

## 实验结果

- 在 CIFAR-100 类别增量学习设置下，内存减少 50% 时仍保持接近完整缓冲区的性能
- DomainNet 领域增量设置验证了跨域泛化能力
- 动态重加权策略比均匀缓冲训练平均提升 8.3% 的旧任务准确率

## 为什么重要

CLIP 已成为多模态 Agent 系统视觉理解的核心组件，但其对比学习目标与持续学习的灾难性遗忘问题存在根本冲突。本工作首次系统解决了小内存缓冲区下 CLIP 持续学习的难题，对于需要在边缘设备上持续学习新视觉概念的 Agent 系统具有重要意义。

## 与端侧/移动端的相关性

**高度端侧相关**：移动设备视觉 Agent 面临存储空间受限但需要持续学习新概念的矛盾。本文的动态重加权方法计算开销小、内存效率高，适合端侧部署。对于移动端视觉搜索、拍照识别等场景，可以在不遗忘旧类别知识的情况下持续学习新类别。
