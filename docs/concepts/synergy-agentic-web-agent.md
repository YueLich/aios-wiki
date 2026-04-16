---
type: concept
tags: [ai-agent, agent-identity, agentic-web, multi-agent, persistent-memory, agent-architecture]
related: [[agent-persistent-identity]], [[exectune-guide-core-policy]], [[clawmobile-agentic]], [[secagent-mobile-gui]], [[emommas-edge-negotiation]]
sources:
  - url: https://arxiv.org/abs/2603.28428
    title: "Synergy: A Next-Generation General-Purpose Agent for Open Agentic Web"
    date: 2026-04-14
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Synergy：开放 Agentic Web 的下一代通用 Agent 架构

> 一个将 Agent 视为"数字社会公民"而非"软件工具"的通用 Agent 架构，围绕三个核心需求设计：开放网络协作、Agent 身份与人格、终身进化。

## 核心问题

当前 AI Agent 系统存在根本性设计缺陷：
- **封闭沙箱**：即使标榜"多 Agent"的系统也局限于内部编排，无法参与开放网络协作
- **无状态函数调用**：Agent 每次会话重置，缺乏跨会话连续性
- **静态能力**：Agent 不从经验中学习，不随时间进化

Synergy 提出：Agent 必须成为**Agentic Citizens（数字公民）**，而非仅仅是软件工具。

## 方法/架构

### 三大设计需求

**1. 开放网络原生协作（Agentic-Web-Native Collaboration）**

从封闭沙箱到开放网络：
- 当前系统（如 AdaptOrch）仅支持内部多 Agent 编排
- Synergy 支持 Agent 加入开放的协作网络
- 基于会话原生编排（session-native orchestration）和仓库支持的工作空间（repository-backed workspaces）
- 社交通信层实现 Agent 间直接交流

**2. Agent 身份与人格（Agent Identity and Personhood）**

从可重置的函数调用到持久社会实体：
- 类型化记忆（typed memory）：结构化的长期记忆系统
- 笔记（notes）：Agent 的工作记录
- 日程（agenda）：Agent 的待办事项和计划
- 技能（skills）：可积累的能力集合
- 持久社会关系（persistent social relationships）：Agent 与其他 Agent 和人类的长期关系

这是对[[agent-persistent-identity]]中多锚点架构的进一步发展——Synergy 将身份从"记忆"扩展到完整的"人格"维度。

**3. 终身进化（Lifelong Evolution）**

从静态能力到经验驱动的学习：
- 主动回忆被奖励的经验（proactively recalls rewarded trajectories）
- 在任务执行、通信和协作三个维度上持续改进
- 不依赖模型重训练，而是运行时的适应性学习

### 系统架构

Synergy 的运行时包含：
- **Orchestrator**：会话原生的任务编排器
- **Workspace**：基于 Git 仓库的持久化工作空间
- **Social Layer**：Agent 间和人机间的社会通信
- **Memory System**：类型化记忆 + 笔记 + 日程
- **Learning Loop**：经验驱动的终身学习机制

## 关键洞察

### 关于 Agent 持久化身份

Synergy 论文引用了相关研究发现：在持续的人机交互中，**用户的依恋模式与人际关系中的依恋模式相似**。人类学研究进一步表明，用户通过反复交互将一致的身份归因于 Agent，而这种归因是依恋形成的中介路径。

**关键推论**：当 Agent 的感知身份被破坏时（如模型更新、平台变化、会话重置），用户信任和依附感受损。这为 Agent 持久化身份提供了强烈的心理学依据。

### 从工具到公民的范式转变

| 维度 | 传统 Agent（工具） | Synergy Agent（公民） |
|------|-----------------|-------------------|
| 协作 | 封闭编排 | 开放网络协作 |
| 身份 | 无状态函数 | 持久人格 |
| 能力 | 静态 | 终身进化 |
| 关系 | 一次性交互 | 持久社会关系 |
| 记忆 | 会话级 | 跨会句话题化记忆 |

## 为什么重要

1. **Agent 生态的方向性指引**：Synergy 定义了 Agent 系统应该朝什么方向发展——从工具到公民
2. **手机端 Agent 的身份连续性**：[[clawmobile-agentic]] 中的手机 Agent 需要跨应用、跨会话的身份连续性
3. **多 Agent 系统的社会动力学**：[[emommas-edge-negotiation]] 中的情感感知多 Agent 系统需要社会关系建模
4. **隐私新维度**：Agent 的持久人格和记忆带来新的隐私挑战（参考[[genai-smartphone-privacy-perception]]）

## 关联

- [[agent-persistent-identity]] — Synergy 的身份系统是多锚点架构的具体实现和扩展
- [[exectune-guide-core-policy]] — ExecTune 的 Guide Model 理念与 Synergy 的技能系统有相似之处
- [[clawmobile-agentic]] — ClawMobile 的手机原生 Agent 设计可借鉴 Synergy 的持久化身份
- [[secagent-mobile-gui]] — SecAgent 的语义上下文提取是 Agent 感知能力的基础
- [[emommas-edge-negotiation]] — EmoMAS 的情感感知多 Agent 系统与 Synergy 的社会关系层互补
- [[pspa-bench-gui-agent]] — 未来的 Agent 基准测试应包含身份连续性和社会交互维度
