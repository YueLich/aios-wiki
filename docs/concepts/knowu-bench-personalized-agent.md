---
type: concept
tags: [基准测试, 移动GUI, Agent个性化, 用户偏好, 主动协助]
related: [[pspa-bench-gui-agent]], [[mga-memory-gui-agent]], [[secagent-mobile-gui]], [[clawmobile-agentic]]
sources:
  - url: https://arxiv.org/abs/2604.08455
    title: "KnowU-Bench: Towards Interactive, Proactive, and Personalized Mobile Agent Evaluation"
    date: 2026-04-09
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# KnowU-Bench: 个性化移动 Agent 在线评测基准

> 42 个通用 GUI 任务 + 86 个个性化任务 + 64 个主动任务，强制 Agent 进行真实偏好推理而非上下文查找。

## 核心问题

现有基准无法捕捉个性化移动 Agent 的真实需求：无法测试 Agent 是否能通过交互引导缺失偏好，也无法测试何时介入 vs 保持沉默。

## 方法/架构

### 三类任务设计

| 任务类型 | 数量 | 评估维度 |
|----------|------|----------|
| 通用 GUI | 42 | 基础操作能力 |
| 个性化任务 | 86 | 偏好推理与个性化执行 |
| 主动任务 | 64 | 何时介入 vs 保持沉默 |

### 关键创新

1. **隐藏用户画像**：不把偏好作为静态上下文传入，只暴露行为日志。Agent 必须从交互中真正推理偏好。
2. **LLM 驱动的用户模拟器**：支持多轮偏好引导对话和主动同意处理。
3. **在线评测协议**：严格遵循时间因果关系，评估增量存储过程中的表现。

## 关键洞察

1. **"偏好推理"≠"偏好查找"**：当偏好需要从行为中推断时，Agent 表现断崖式下降。当前 Agent 缺乏真正的用户建模能力。
2. **主动协助的时机选择极难**：过早介入让用户烦躁，过晚介入错过最佳时机。
3. **用户模拟器是可扩展评测的关键**：没有 LLM 驱动的模拟器，无法大规模评估多轮偏好引导交互。

## 为什么重要

端侧 AI Agent 的终极形态是"懂你的助手"，而非"听话的工具"。KnowU-Bench 为这个方向提供了第一个系统化的评测框架。

## 关联
- [[pspa-bench-gui-agent]] — KnowU-Bench 扩展了 PSPA 的个性化维度
- [[mga-memory-gui-agent]] — 记忆驱动 Agent 是偏好推理的基础
- [[secagent-mobile-gui]] — 安全约束下的个性化执行
- [[clawmobile-agentic]] — 原生 Agent 架构需要个性化能力
