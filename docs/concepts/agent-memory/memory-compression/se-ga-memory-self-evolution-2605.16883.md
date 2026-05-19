---
title: "SE-GA: Memory-Augmented Self-Evolution for GUI Agents"
arXiv: 2605.16883
date: 2026-05-16
tags: [memory-compression, self-evolution, GUI-agents, policy-learning]
reviewer: auto
source: arXiv API
---

## 摘要

Autonomous Graphical User Interface (GUI) agents often struggle with multi-step tasks due to constrained context windows and static policies that fail to adapt to dynamic environments. To address these limitations, this work proposes the Self-Evolving GUI Agent (SE-GA), a novel framework that integrates hierarchical memory structures with an iterative self-improvement mechanism. At the core of our approach is Test-Time Memory Extension (TTME), which facilitates long-term planning by dynamically retrieving episodic, semantic, and experiential memories to provide salient contexts during inference. To ensure continuous learning, we introduce Memory-Augmented Self-Evolution (MASE), which is a training pipeline that adopts the data collected by TTME to stabilize and enhance the agent's foundational policy. Extensive evaluations across both offline and online benchmarks demonstrate SE-GA achieves state-of-the-art performance, reaching success rates of 89.0\% on ScreenSpot and 75.8\% on the challenging AndroidControl-High dataset. Furthermore, significant improvements on the AndroidWorld benchmark highlight the superior generalization to dynamic environments. Open source code: https://github.com/jinshilong-dev/SE-GA

## 核心贡献

1. **提出Se方法** — 针对现有记忆系统在自进化能力方面的不足
2. **关键设计** — 集成记忆增强的自我进化框架
3. **实验验证** — 在GUI代理任务上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：使GUI代理能够通过记忆积累实现自我进化
- **实践价值**：增强了代理对动态环境的适应能力

## 与端侧/移动端的相关性

GUI自动化对移动端应用测试有潜在价值

## 参考文献

（参考文献待从原文补充）
