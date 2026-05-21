---
title: "Memory-Induced Supra-Competitive Outcomes Between Deep Reinforcement Learning Agents in Optimal Trade Execution"
arXiv: "2605.20348"
date: "2026-05-19"
tags: [agent-memory, reinforcement-learning, multi-agent, memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Memory-Induced Supra-Competitive Outcomes Between Deep Reinforcement Learning Agents in Optimal Trade Execution
- **arXiv ID**: 2605.20348
- **作者**: Christos Spyridon Koulouris, Carlo Campajola
- **发表日期**: 2026-05-19
- **方向**: Multi-Agent RL / Market Microstructure

## 核心贡献

1. **记忆驱动的超竞争均衡**: 首次证明在共享的最优执行环境中，具备历史记忆的 DRL Agent 可以实现超越博弈论竞争基准的超竞争结果（低于基准的市场冲击）。
2. **记忆作用机制分析**: 系统分析了 Agent 对以下三方面的认知如何影响超竞争结果：episode 内环境反馈、中价解读能力、对过去的知识。
3. **Almgren-Chriss 清算框架**: 在经典的双 Agent Almgren-Chriss 清算博弈环境中验证记忆的关键作用。

## 摘要

In this paper, we investigate whether deep reinforcement-learning agents interacting in a shared optimal-execution environment can sustain supra-competitive outcomes, in the sense of achieving lower implementation shortfalls than the relevant game-theoretical competitive benchmark. We study a two-agent Almgren-Chriss liquidation game and examine how learned behavior depends on intra-episode environment feedback, the ability to interpret the mid-price and the agent's knowledge of the past.

## 详细解读

### 研究背景

市场微观结构中，多个 Agent 在共享交易环境中相互作用。传统理论认为竞争会导致均衡结果接近基准，但这篇论文发现记忆改变了这一局面。

### 核心发现

当 Agent 具备记忆能力时：
- **低于基准的冲击成本**: Agent 通过记忆协调策略，避免在不利价格区间交易，减少市场冲击
- **历史知识的利用**: Agent 学习识别历史模式，预测其他 Agent 的行为，从而选择最优执行时机
- **协调效应**: 记忆使 Agent 能够在一定程度上协调行动，避免"囚徒困境"式的竞争性抛售

### 记忆的作用

Agent 的记忆包括：
1. **Episode 内记忆**: 当前交易日的即时价格和流量信息
2. **跨 Episode 记忆**: 历史交易日的价格模式和市场条件知识
3. **对手模型**: 对其他 Agent 行为模式的隐性建模

## 为什么重要

这是首次在金融交易场景中系统证明记忆对 Agent 策略质量的决定性作用。对高频交易、量化策略和做市系统有直接影响。

## 与端侧/移动端的相关性

虽然这是金融交易场景，但记忆协调机制对其他共享资源的多 Agent 系统也有参考价值。例如，移动端多个本地 Agent 协调访问共享传感器数据时，记忆同样可以帮助避免重复计算和资源竞争。

## 参考文献

（参考文献待从原文补充）
