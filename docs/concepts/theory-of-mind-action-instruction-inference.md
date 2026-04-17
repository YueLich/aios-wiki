---
type: concept
tags: [multi-agent, agent-collaboration, theory-of-mind, instruction-inference, reasoning, 人机协作]
related: [[clawmobile-agentic]], [[secagent-mobile-gui]], [[mga-memory-gui-agent]], [[long-horizon-task-mirage]], [[synergy-agentic-web-agent]]
sources:
  - url: https://arxiv.org/abs/2507.02935
    title: "Theory of Mind in Action: The Instruction Inference Task in Dynamic Human-Agent Collaboration"
    date: 2025-07-04
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Theory of Mind in Action: 指令推理与动态人机协作

> 提出 Instruction Inference Task，检验 Agent 在不完整/模糊指令下推断人类隐含意图的能力——这是 mobile agent 真正理解用户需求的关键能力。

## 核心问题

Mobile GUI Agent 目前依赖精确、完整的指令描述（如"点击设置→显示→亮度"），但现实场景中用户的指令往往是模糊的、不完整的、甚至有歧义的。Agent 需要具备 Theory of Mind（心智理论）能力，从共享上下文中推断出用户的真实意图。

当前人机协作的瓶颈不在于执行能力，而在于**理解意图**——Agent 需要从不完整的指令中推断出"未说出口的部分"。

## 方法/架构

论文提出了 **Instruction Inference Task** 作为评估框架：

- **场景设计**：Agent 与人类（principal）协作完成任务，人类给出的指令可能是不完整或模糊的
- **推理要求**：Agent 必须从共享上下文（shared context）中推断出未明确表达的意图
- **关键挑战**：如何在动态交互中维护对人类意图的持续理解

这与传统 NLU 任务不同——它强调的是**动态协作场景中的意图推断**，而非静态的指令解析。

## 实验结果

论文通过 human-agent 团队实验展示了：
- Agent 在缺乏明确指令时的失败模式
- 共享上下文（shared context）对意图推断的重要性
- Theory of Mind 能力的缺乏是当前 Agent 系统的主要瓶颈

## 关键洞察

1. **指令 ≠ 意图**：用户的指令是意图的部分表达，Agent 需要补全缺失的部分
2. **共享上下文是关键**：没有共享的背景知识，意图推断是不可能的
3. **动态性**：协作场景中指令和意图会随交互演化，Agent 需要持续更新理解
4. **对 mobile agent 的启示**：手机端 Agent 面对的是用户日常的模糊交互（"帮我弄一下那个"），ToM 能力是实现自然交互的前提

## 为什么重要

手机端 AI Agent 要真正融入用户日常生活，不能依赖结构化的精确指令。用户会说"把那个发给老张"或"帮我订个好吃的"——这些模糊指令需要 Agent 具备推断意图的能力。本论文为评估和构建具备 ToM 能力的 Agent 提供了理论框架和实验方法，对 mobile agent 的交互设计有直接指导意义。

## 关联
- [[clawmobile-agentic]] — ClawMobile 的原生 Agent 架构需要集成 ToM 能力
- [[secagent-mobile-gui]] — GUI Agent 的屏幕理解是 ToM 的视觉基础
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent 可以通过交互历史提升意图推断
- [[long-horizon-task-mirage]] — 长程任务中的意图漂移是 ToM 的挑战
- [[synergy-agentic-web-agent]] — Web Agent 的多步骤推理也依赖意图理解
