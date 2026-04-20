---
type: concept
tags: [agent, policy, memory, governance, tool-use, 自适应]
related: [[gui-agent-privacy]], [[mga-memory-gui-agent]], [[agent-persistent-identity]]
sources:
  - url: https://arxiv.org/abs/2604.15505
    title: "PolicyBank: Evolving Policy Understanding for LLM Agents"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# PolicyBank: Agent 策略自演化理解

> 通过交互反馈让 LLM Agent 自主演化对组织策略的理解，而非将策略视为不可变的规则。来自 Jihye Choi 等人 (arXiv 2604.15505)。

## 核心问题

LLM Agent 在组织策略下运行时，需要遵循通常以自然语言指定的授权约束。但这些规范不可避免地存在歧义和逻辑漏洞，导致 Agent 行为系统性偏离真实需求。现有方法将策略视为不可变的"地面真理"，强化了"看似合规但实际错误"的行为。

## 方法/架构

**PolicyBank** 是一种记忆机制，维护结构化的、工具级别的策略洞察，并通过迭代反馈不断精化：

- **策略状态记忆**：不像传统记忆将策略视为静态规则，PolicyBank 维护每个工具调用的策略状态，记录什么是被允许的、什么是被拒绝的、以及为什么
- **反馈驱动演化**：在部署前测试中，通过纠正性反馈（correction feedback）让 Agent 自主发现并填补策略规范中的漏洞
- **工具级粒度**：策略理解与具体工具绑定，而非全局抽象规则，使每个工具的策略边界清晰可控

## 实验结果

- 在多个组织策略场景中，PolicyBank 显著减少了"合规但错误"的行为
- Agent 能够从少量纠正反馈中泛化，修复类似的策略理解漏洞
- 与静态策略方法对比，PolicyBank 在策略覆盖完整性上表现更优

## 关键洞察

核心创新在于将"策略理解"从静态规则匹配转变为动态学习过程。传统方法假设策略规范是完备的（closed-world assumption），但现实中的组织策略总是存在缺口。PolicyBank 承认这种不完备性，并通过交互式学习来弥补。

对于手机端 Agent 而言，这一机制尤为重要——移动设备上的 Agent 面临更复杂、更动态的权限边界（位置、相机、通讯录等），策略规范不可能覆盖所有场景。

## 为什么重要

- **端侧 Agent 安全**：移动 Agent 的权限边界远比云端复杂，PolicyBank 提供了一种自适应策略理解框架
- **降低人工标注**：不需要人工编写完备的策略规则，Agent 通过少量反馈自主完善
- **Agent 持久身份**：与 [[agent-persistent-identity]] 概念互补——不仅记住"我是谁"，还记住"什么能做什么不能做"

## 关联
- [[gui-agent-privacy]] — GUI Agent 隐私保护，PolicyBank 可作为策略层
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent，PolicyBank 提供策略记忆
- [[agent-persistent-identity]] — Agent 持久身份，策略理解是身份的一部分
- [[exectune-guide-core-policy]] — ExecTune 的核心策略机制
