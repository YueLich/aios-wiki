---
title: "Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks"
arXiv: 2604.24637
date: 2026-04-27
authors: ["Kevin McKee", "Thomas Hazy", "Yicong Zheng"]
tags: [agent-memory, continual-learning, neuro-inspired, parameter-isolation, cortex]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.24637
- **作者**: Kevin McKee, Thomas Hazy, Yicong Zheng
- **提交日期**: 2026-04-27
- **方向**: 持续学习 / 神经启发 / 参数隔离

## 摘要（全文翻译）

块序贯持续学习要求单个模型既保护先验解决方案免受灾难性遗忘，又能在推理时高效推断哪个先验解决方案与当前输入匹配（无任务标签）。本文提出**功能任务网络（FTN）**，一种受哺乳动物新皮层结构和动力学模式启发的参数隔离方法。

## 核心贡献

1. **受皮层启发的参数隔离**：用新皮层的模块化和动态招募机制解决灾难性遗忘
2. **无任务标签的推理时识别**：模型自动判断当前输入应使用哪个先验解决方案
3. **功能任务网络**：将每个任务封装为独立的功能模块，新任务动态实例化新模块

## 为什么重要

FTN 将神经科学的发现（新皮层的模块化招募机制）转化为 CL 的工程解决方案。核心洞察：人类新皮层不会"覆盖"旧知识，而是招募新的神经资源来处理新任务，同时保持旧资源的完整性。

## 与端侧/移动端的相关性

参数隔离方法对端侧持续学习有吸引力：每个任务/用户的参数隔离使得推理时无需任务标签，且可以单独更新或回滚特定任务，不影响其他任务。
