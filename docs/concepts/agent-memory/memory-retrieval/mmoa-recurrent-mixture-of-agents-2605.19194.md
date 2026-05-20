---
title: "MMoA: An AI-Agent framework with recurrence for Memoried Mixure-of-Agent"
arXiv: 2605.19194
date: 2026-05-18
tags: [agent-memory, multi-agent]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **标题**: MMoA: An AI-Agent framework with recurrence for Memoried Mixure-of-Agent
- **arXiv ID**: 2605.19194
- **发表日期**: 2026-05-18
- **作者**: Rui Chu
- **方向**: cs.CL

## 摘要（英译中）

混合 Agent（Mixture-of-Agents，MoA）框架通过聚合多个 Agent 的输出，在提升大语言模型性能方面展现出潜力。然而，现有 MoA 系统通常依赖静态路由器，无法充分捕捉跨聚合层的时间维度和上下文依赖关系。为解决这一局限，本文提出 MMoA，一种循环 MoA 架构，将基于 LSTM 的门控机制集成到 Agent 选择过程中。循环路由器基于当前输入和历史路由决策自适应地调节各 Agent 的贡献，实现更符合上下文的聚合。在 AlpacaEval 2.0、MT-Bench 和 Arena-Hard 等标准指令跟随基准上的评估表明，MMoA 在保持与传统 MoA 相当的精度的同时，通过动态激活更少的 Agent 降低了计算开销。例如，在 AlpacaEval 2.0 上，MMoA 达到 58.0% 的胜率（对比 MoA 的 59.8%），同时运行时效率提升最高达 4.6%。这些结果表明 MMoA 为自适应多 Agent LLM 系统提供了一种可扩展且高效的方案。

## 核心贡献

1. **循环 MoA 架构（MMoA）**：引入 LSTM 门控机制，使路由器能够记忆历史路由决策，并根据历史上下文自适应调节 Agent 贡献。

2. **动态 Agent 激活**：非静态激活所有 Agent，而是通过 LSTM 门控动态决定激活哪些 Agent，提升计算效率。

3. **上下文感知聚合**：捕捉跨聚合层的时间依赖关系，比静态路由器更适应复杂的多轮任务。

4. **无需额外训练**：LSTM 门控可基于现有 Agent 输出进行轻量微调或作为即插即用模块。

## 关键发现

- 静态路由器忽略了路由决策的历史依赖关系
- LSTM 门控可以在不显著牺牲精度的前提下显著降低计算开销
- 历史路由上下文对复杂多跳任务尤其有价值
- 动态 Agent 激活提供了一种优雅的效率-精度权衡

## 为什么重要

MMoA 将"记忆"概念引入多 Agent 系统的路由决策，是 MoA 领域的重要演进。虽然其"记忆"更多体现在路由历史的建模上而非 Agent 自身的经验记忆，但对记忆增强型多 Agent 系统有重要启发——Agent 不仅需要记忆个体经验，还需要记忆协作模式。

## 与移动端/端侧的相关性

MMoA 的动态 Agent 激活机制对端侧部署有直接价值：通过智能选择激活哪些 Agent 而不是全量激活，可以显著降低端侧推理的计算和内存开销。其 LSTM 门控的轻量设计也适合移动端资源约束。

## 参考文献

参考文献待从原文补充。详情见 https://arxiv.org/abs/2605.19194
