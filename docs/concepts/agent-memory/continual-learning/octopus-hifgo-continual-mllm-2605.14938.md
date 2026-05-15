---
title: "Octopus: History-Free Gradient Orthogonalization for Continual Learning in Multimodal Large Language Models"
arXiv: 2605.14938
date: 2026-05-14
tags: [agent-memory, continual-learning, multimodal, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文提出 Octopus，一种基于无历史梯度正交化（HiFGO）的两阶段持续学习框架，用于解决多模态大语言模型（MLLMs）在顺序学习新任务时的灾难性遗忘问题。Octopus 通过在梯度层面强制正交性来隔离任务适应与正则化，避免存储历史数据，同时在 UCIT 基准上达到 SOTA，Avg 和 Last 指标分别提升 2.14% 和 6.82%。

## 核心贡献

1. **HiFGO（无历史梯度正交化）**：在不依赖历史任务数据的前提下，通过梯度级正交性防止参数干扰，无需 replay buffer 或架构扩展。

2. **两阶段微调策略**：将任务适应与正则化解耦，实现塑性与稳定性的原则性平衡——第一阶段完成任务适应，第二阶段应用梯度正交化约束。

3. **隐私与效率优势**：rehearsal-based 方法依赖存储历史数据，存在隐私和存储开销；Octopus 完全无需存储，实现真正的"无记忆"持续学习。

4. **SOTA 性能**：在 UCIT 基准上，Octopus 在 Avg 和 Last 指标上分别超越先前最佳方法 2.14% 和 6.82%。

## 为什么重要

现有持续学习方法在 MLLMs 上面临三重困境：架构方法计算开销大且泛化差，rehearsal 方法存在隐私和存储问题，而纯正则化方法不足以完全防止参数干扰。Octopus 通过创新的梯度正交化机制，首次在无需历史数据的情况下实现了高效、隐私安全的持续学习，对端侧/移动端部署的多模态 AI 助手具有重要意义。

## 与移动端/端侧的相关性

移动端多模态助手需要频繁学习用户的新偏好和本地场景知识，但设备存储有限且隐私敏感。Octopus 的无 replay、无额外架构开销特性使其特别适合端侧部署——模型可以在保护用户隐私的前提下持续适应个人使用模式，而不占用宝贵的设备存储空间。

## 参考文献

（参考文献待从原文补充）
