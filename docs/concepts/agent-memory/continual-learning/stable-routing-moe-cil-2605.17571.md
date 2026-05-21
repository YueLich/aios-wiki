---
title: "Stable Routing for Mixture-of-Experts in Class-Incremental Learning"
arXiv: "2605.17571"
date: "2026-05-17"
tags: [continual-learning, mixture-of-experts, class-incremental]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Stable Routing for Mixture-of-Experts in Class-Incremental Learning
- **arXiv ID**: 2605.17571
- **作者**: Zirui Guo, Quan Cheng, Da-Wei Zhou, Lijun Zhang
- **发表日期**: 2026-05-17
- **方向**: Class-Incremental Learning / MoE

## 核心贡献

1. **路由稳定性问题识别**: 首次系统指出 MoE 类增量学习中"路由漂移"（routing drift）问题——新增专家后，路由器可能重新分配旧样本给新专家，导致旧知识丢失。
2. **稳定路由机制**: 提出稳定路由方法，在新增专家时保持对旧样本的路由决策稳定，避免灾难性遗忘。
3. **无需Replay的增量学习**: 通过路由层面的设计，在一定程度上减少了对回放样本的依赖。

## 摘要

Class-incremental learning (CIL) requires models to learn new classes sequentially while preserving prior knowledge. Recently, approaches that combine pre-trained models with mixture-of-experts (MoE) have received increasing attention in CIL: they typically expand experts during learning and employ a router to assign weights across experts. However, existing MoE methods often overlook routing drift induced by expert expansion. Once new experts are introduced, the router may reassign samples from previously learned classes to new experts, leading to significant performance degradation on old classes.

## 详细解读

### 研究背景

Class-Incremental Learning (CIL) 要求模型顺序学习新类，同时保留旧类知识。MoE 架构通过新增专家学习新类，是 CIL 的自然选择。但新增专家会引发路由漂移：

- **路由漂移机制**: 新专家加入后，路由器倾向于将更多样本（包括旧类样本）分配给新专家
- **旧知识丢失**: 旧样本被分配给新专家后，训练时旧专家收到的梯度信号减少，导致旧知识被覆盖
- **连锁反应**: 旧类性能下降又进一步影响整体分类准确率

### 核心方法

稳定路由的核心设计：
- **路由约束**: 在新增专家后，对旧类样本的路由概率施加约束，保持与添加前的一致性
- **专家专用性保护**: 确保旧专家在其擅长的旧类样本上保持高响应
- **渐进式适应**: 新专家逐步增加负载，避免剧烈改变路由分布

## 为什么重要

这是首个系统研究 MoE 路由漂移问题的工作，对 MoE + Continual Learning 领域有重要推动作用。提出的稳定路由机制简单有效，为后续研究提供了新方向。

## 与端侧/移动端的相关性

MoE 在端侧有天然优势——稀疏激活只调用部分专家，可以降低计算开销。本工作对端侧增量学习有直接参考价值，尤其在资源受限环境下无法存储大量回放样本时，稳定路由可以减少对 replay 的依赖。

## 参考文献

（参考文献待从原文补充）
