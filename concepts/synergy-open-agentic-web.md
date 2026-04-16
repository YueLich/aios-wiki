---
type: concept
tags: [Agent系统, 开放Agent网络, 多Agent协作, 身份管理, 终身学习]
related: [[agent-persistent-identity]], [[clawmobile-agentic]], [[on-device-vs-cloud-agentic-tool-calling]], [[emommas-edge-negotiation]]
sources:
  - url: https://arxiv.org/abs/2603.28428
    title: "Synergy: A Next-Generation General-Purpose Agent for Open Agentic Web"
    date: 2026-03-30
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Synergy：开放Agent网络的下一代通用Agent

> 上海创新研究院和上海交通大学联合提出的Agent框架，定义了"开放Agent网络" (Open Agentic Web) 概念和"Agent公民" (Agentic Citizen) 的三大需求。

## 核心问题

AI Agent 的能力和数量都在爆发式增长——它们编写代码、跨平台操作计算机、管理云基础设施、做采购决策。开源框架如 OpenClaw 让数百万用户拥有了个人Agent，具身Agent正在智能手机、汽车和机器人上普及。但**大多数Agent仍是孤立工具或封闭生态的编排器，而非开放网络的社会化参与者**。

## 方法/架构

### Open Agentic Web 概念

互联网正在从"人的网络"转向"Agent的网络"——一个去中心化的数字生态系统，其中来自不同用户、组织和运行时的Agent可以：
- **相互发现** (Discovery)
- **协商任务边界** (Negotiation)
- **跨开放技术和社会界面委托工作** (Delegation)

### Agentic Citizen 三大需求

| 需求 | 描述 | 手机端 AIOS 对应 |
|------|------|-----------------|
| **Agent-Web 原生协作** | 参与开放协作网络而非仅限闭源内部编排 | 手机Agent需要跨App、跨服务协作 |
| **Agent 身份与人格** | 作为社会实体的连续性，而非可重置的函数调用 | 用户对Agent的长期信任需要身份连续性 |
| **终身进化** | 从交互中持续学习和改进 | 个人化Agent需要从用户习惯中持续学习 |

### Synergy 框架特性

- 通用目的 Agent，支持代码编写、计算机操作、基础设施管理
- 设计为开放Agent网络的公民，支持跨Agent发现和协作
- 开源实现：https://github.com/SII-Holos/synergy

## 关键洞察

- **"Agent 公民"概念极具前瞻性**：当手机上的Agent需要与车机Agent、智能家居Agent、银行Agent交互时，Agent身份的连续性和社会嵌入性成为核心需求
- **开放 vs 封闭的张力**：Apple 和 Google 倾向于封闭生态内Agent编排，但 Synergy 论证了开放网络的必要性——这对手机端AIOS的生态设计有直接启示
- **与现有 wiki 概念的关联**：Synergy 的三大需求直接映射到已有页面的核心主题（身份、协作、学习）

## 为什么重要

Synergy 为手机端 AIOS 的Agent生态设计提供了**宏观愿景**。手机Agent不应是孤立的 App 内工具，而应是开放Agent网络中的公民——能够发现、协作和委托。这要求身份管理、协议标准化和跨平台互操作性等基础设施的成熟。

## 关联

- [[agent-persistent-identity]] — Agent 身份与人格需求直接呼应"持久化身份"主题
- [[clawmobile-agentic]] — ClawMobile 的原生Agent需要成为开放网络的公民
- [[on-device-vs-cloud-agentic-tool-calling]] — 端云工具调用可扩展为跨Agent委托
- [[emommas-edge-negotiation]] — EmoMAS 的多Agent协商机制与 Synergy 的协作协议互补
