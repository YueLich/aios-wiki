---
title: "GR4CIL: Gap-compensated Routing for CLIP-based Class Incremental Learning"
arXiv: 2604.17822
date: 2026-04-20
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# GR4CIL: Gap-compensated Routing for CLIP-based Class Incremental Learning

## 论文基本信息

- **作者**: Tianqi Wang, Jingcai Guo
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2604.17822
- **代码**: （待补充）

## 核心贡献

1. **任务判别与知识路由结合**: 提出 GR4CIL 框架，将任务判别与知识路由相结合用于 CLIP-based 增量学习。
2. **正交补偿机制**: 引入正交补偿机制来缓解模态差距导致的偏差，增强任务内区分性，并扩大正确任务与竞争任务之间的分数差距。
3. **CLIP 零样本泛化能力保留**: 在保持 CLIP 零样本泛化能力的同时实现可靠的任务感知路由。

## 研究背景与问题

类别增量学习（Class-Incremental Learning, CIL）旨在持续学习新类别同时保留已学知识。CLIP 模型因其强大的泛化能力在 CIL 中展现潜力，但现有方法面临两个关键挑战：

- **共享参数适应**导致旧知识漂移（old-knowledge drift）
- **任务特定知识组织**导致跨任务响应校准不佳，使可靠路由困难

## 核心方法

GR4CIL 框架的核心设计：

1. **任务特定视觉知识保留**: 保持任务特定的视觉知识
2. **增量稳定的共享语义空间**: 维护一个增量稳定的共享文本语义空间，减少跨任务干扰
3. **正交补偿机制**: 
   - 缓解模态差距（modality gap）带来的偏差
   - 增强任务内区分性
   - 扩大 ground-truth 任务与竞争任务之间的分数差距

## 实验结果

在多个基准数据集上的实验表明，GR4CIL 一致性地优于强基线方法。

## 为什么重要

这篇论文揭示了 CLIP 模型在持续学习场景下的关键挑战——模态差距与知识漂移的正交补偿机制，为构建更可靠的增量学习系统提供了新思路。

## 与移动端/端侧相关性

CLIP 模型在端侧设备（如移动端图片分类、AR 场景识别）中有应用前景。GR4CIL 的路由机制可以在增量加入新类别时减少对已有知识的破坏，提升端侧模型的可扩展性。
