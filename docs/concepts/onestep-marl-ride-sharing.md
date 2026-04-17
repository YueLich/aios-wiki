---
type: concept
tags: [multi-agent, reinforcement-learning, ride-sharing, grpo, agent-architecture]
related: [[clawmobile-agentic]], [[aipc-qualcomm-deployment-agent]], [[mga-memory-gui-agent]]
sources:
  - url: https://arxiv.org/abs/2507.15351
    title: "One Step is Enough: Multi-Agent Reinforcement Learning based on One-Step Policy Optimization"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# OSPO: 单步策略优化的多智能体强化学习

> 提出基于单步组奖励的多智能体策略优化方法，绕过价值函数估计，在网约车调度任务中优于 GRPO 和 PPO 基线

## 核心问题

网约车平台的订单调度是典型的多智能体问题：数百/数千辆自动驾驶车辆需要实时匹配乘客订单。传统 MARL 方法（如 DTDE）依赖价值函数估计（Q-value/V-value），在大规模、高不确定性环境中估计误差严重，导致训练不稳定和协作失效。

## 方法：从 GRPO 到 OSPO

### GRPO（Group Relative Policy Optimization）
- 借鉴 RLHF 中的 GRPO 方法，用组平均回报替代 PPO 中的 V-value 基线
- 消除了 critic 估计误差，减少训练偏差
- 适用于同质 AV 车队（所有车辆策略相同）

### OSPO（One-Step Policy Optimization）
核心创新：证明了在同质车队假设下，**只需一步组奖励即可训练最优策略**。

```
传统 MARL: 需要完整轨迹 → 估计 V-value → 高偏差
GRPO:      需要完整轨迹 → 组平均回报 → 无 critic 偏差
OSPO:      只需一步奖励 → 组平均 → 最简洁高效
```

### 为什么一步就够？
关键洞察：在同质车队中，所有智能体共享相同策略。组内平均回报已经包含了环境的统计信息，不需要多步轨迹来估计价值函数。

## 实验结果

| 方法 | 拾取时间 | 服务订单数 | 训练稳定性 |
|------|---------|-----------|-----------|
| PPO (baseline) | 基线 | 基线 | 不稳定 |
| GRPO | 更优 | 更优 | 稳定 |
| OSPO | **最优** | **最优** | **最稳定** |

- 使用真实网约车数据集
- 仅需简单 MLP 网络（无需复杂架构）
- OSPO 在所有场景中均优于 GRPO

## 关键洞察

1. **同质性是关键假设**：所有 AV 共享相同策略使得一步优化可行——异质车队中该假设不成立
2. **简化 ≠ 弱化**：OSPO 证明了更简单的训练信号（一步奖励）在特定条件下等价于完整轨迹
3. **对移动 AIOS 的启示**：手机端多 Agent 系统（如多个 AI 助手协作）同样可能是同质或近同质的，OSPO 思路可迁移
4. **GRPO 的跨领域迁移**：从 RLHF（语言模型对齐）到 MARL（多智能体调度）的成功迁移表明 GRPO 框架的通用性

## 为什么重要

这项工作对移动 AIOS 中的多 Agent 协作设计有直接启发：
- 手机上的多个 AI Agent（助手、推荐、搜索等）通常是同质架构 → OSPO 的一步优化思路适用
- 简化训练信号降低了端侧 Agent 联合优化的计算成本
- 组相对优化消除了价值函数估计——这在资源受限的端侧环境中尤为重要

## 关联
- [[clawmobile-agentic]] — 原生 Agent 架构中的多 Agent 协调可借鉴 OSPO 的同质优化思路
- [[aipc-qualcomm-deployment-agent]] — 部署 Agent 的多阶段协调与多智能体优化有共通之处
- [[mga-memory-gui-agent]] — GUI Agent 中的多任务分配可视为多智能体问题
