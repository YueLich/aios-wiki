---
type: concept
tags: [gui-agent, memory, observation-centric, mobile, interaction]
related: [[secagent-mobile-gui]], [[clawmobile-agentic]], [[edgeflow-cold-start]]
sources:
  - "[arXiv] MGA: Memory-Driven GUI Agent for Observation-Centric Interaction"
created: 2026-04-14
---

# MGA：记忆驱动的 GUI Agent

## 概念定义

MGA（Memory-Driven GUI Agent）提出了一种以观察为中心（Observation-Centric）的交互范式。不同于传统 Agent 依赖预定义的 action space，MGA 通过维护屏幕观察的记忆来理解界面状态变化，从而做出更灵活的交互决策。

## 为什么重要

当前移动 GUI Agent 面临的核心挑战之一是界面状态的动态性——同一个 App 在不同时间、不同账户下的界面可能完全不同。MGA 的创新在于：
1. **观察驱动**：不假设固定的界面结构，而是实时理解当前屏幕
2. **记忆增强**：跨步骤维持上下文，避免重复探索
3. **泛化能力**：对未见过的界面变化有更强的适应力

这解决了 [[secagent-mobile-gui]] 关注的语义理解问题的一个关键子问题：如何在不预知界面布局的情况下有效交互。

## 与手机端 AIOS 的关联

手机是动态性最强的计算平台——App 频繁更新，个性化设置差异巨大。记忆驱动的 Agent 能更好地适应这种变化。与 [[edgeflow-cold-start]] 中的冷启动优化结合，可以实现"首次使用-快速学习-持续优化"的 Agent 体验。

## 相关概念

- [[secagent-mobile-gui]] — 语义上下文理解
- [[clawmobile-agentic]] — 原生 Agent 系统
- [[edgeflow-cold-start]] — 冷启动优化
