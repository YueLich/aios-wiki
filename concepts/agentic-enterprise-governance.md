---
type: concept
tags: [agent, governance, enterprise, sprawl, management, maturity-model]
related: [[semantic-consensus-multi-agent]], [[agent-persistent-identity]], [[conjunctive-prompt-attacks-multi-agent]]
sources:
  - url: https://arxiv.org/abs/2604.16338
    title: "Governing the Agentic Enterprise: A Governance Maturity Model for Managing AI Agent Sprawl in Business Operations"
    date: 2026-04-18
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Agent 治理成熟度模型：管理企业 AI Agent 扩张

> 2025 年 79% 的组织已采用 Agentic AI，市场预计从 2026 年的 85 亿美元增长到 2030 年的 450 亿美元。但 Agent 数量的快速扩张带来了"Agent 蔓延"（Agent Sprawl）问题。本文提出一个治理成熟度模型，对手机端 AIOS 的 Agent 管理架构设计有直接参考价值。

## 核心问题

Agentic AI 与传统 AI 系统的本质区别在于**自主性**：Agent 可以自主规划多步策略、选择和调用工具、执行复杂工作流，几乎不需要人工干预。这种自主性在带来价值的同时，也带来了治理挑战：

- **Agent 蔓延**：组织内大量独立部署的 Agent 缺乏统一管理
- **权限失控**：Agent 的工具调用权限可能超出预期范围
- **审计困难**：自主 Agent 的决策过程难以追溯和审计
- **冲突与冗余**：多个 Agent 可能执行重叠甚至冲突的任务

## 方法/架构

论文提出了一个五级治理成熟度模型：

### Level 1: Ad Hoc（临时性）
- Agent 以临时方式部署，无统一管理
- 缺乏标准化的部署、监控和审计流程

### Level 2: Managed（受管理的）
- 基础的 Agent 注册和发现机制
- 简单的权限控制和日志记录

### Level 3: Governed（受治理的）
- 统一的 Agent 生命周期管理
- 策略驱动的权限控制
- 自动化的合规检查

### Level 4: Orchestrated（编排的）
- Agent 间的协调和冲突避免
- 资源优化和负载均衡
- 端到端的工作流可视化

### Level 5: Autonomous Governance（自治治理）
- 自我监督和自我优化的 Agent 生态
- 基于反馈的治理策略自动调整
- 弹性故障恢复和自愈

## 实验结果

- 74% 的部署 Agent 的高管在第一年内实现投资回报
- 但只有少数组织达到 Level 3+ 的治理成熟度
- 最常见的治理失败模式：权限过度授予、缺乏审计追踪、Agent 间冲突

## 关键洞察

- **治理是规模化前提**：没有治理框架的 Agent 部署在小规模时运行良好，但规模扩大后必然失控
- **手机端的类比**：手机端 App Agent 的增长轨迹类似于企业 Agent 扩张——每个 App 都有自己的 Agent，系统需要统一治理
- **权限最小化原则**：Agent 应该只获得完成任务所需的最小权限集，而非全系统访问权限
- **审计不可妥协**：Agent 的每个决策和工具调用都需要可追溯的审计日志

## 为什么重要

手机端 AIOS 正在进入 Agent 爆发期：
1. **系统级 Agent**：iOS Apple Intelligence、Android Gemini、小米 HyperAI 等
2. **App 级 Agent**：每个 App 可能部署自己的 Agent
3. **用户自定义 Agent**：用户可能创建自定义自动化 Agent

这些 Agent 需要统一的治理框架——权限管理、冲突避免、审计追踪、生命周期管理。本文的成熟度模型为手机端 Agent 治理架构提供了设计蓝图。

## 关联

- [[semantic-consensus-multi-agent]] — Agent 间冲突检测是治理的关键组件
- [[agent-persistent-identity]] — Agent 身份管理是治理的基础
- [[conjunctive-prompt-attacks-multi-agent]] — 安全治理需要防御提示攻击
- [[gui-agent-privacy]] — Agent 治理中的隐私保护
