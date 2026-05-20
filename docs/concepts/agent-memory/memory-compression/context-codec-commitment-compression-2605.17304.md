---
title: "Compress the Context, Keep the Commitments: A Formal Framework for Verifiable LLM Context Compression"
arXiv: 2605.17304
date: 2026-05-17
tags: [agent-memory, memory-compression, context-compression, commitments]
reviewer: auto
source: arXiv API
---

## 核心贡献

本文提出 **Context Codec**，首个承诺级别（Commitment-Level）的 LLM 上下文压缩框架。核心洞察：LLM 上下文不仅是 token 序列，更是**承诺集合**——包含目标、约束、决策、偏好、工具结果、检索证据、产物和安全边界。

现有上下文管理方法（截断、检索、摘要、记忆系统、token 级提示压缩）很少明确指定哪些语义承诺必须保留，以及如何衡量其保存情况。

**Context Codec 方案：**
- 承诺级别压缩框架，区分并保留关键语义承诺
- 可验证的压缩保真度评估
- 在压缩上下文中追踪承诺满足情况

## 为什么重要

长时域对话中，上下文管理直接影响 Agent 的长期目标追踪和决策一致性。传统方法可能导致关键承诺在压缩中丢失，影响系统可靠性。Context Codec 通过形式化承诺概念，为压缩提供了理论基础。

## 与端侧/移动端相关性

- **长时域 Agent 的可靠性**：承诺追踪对端侧 Agent 的多轮交互尤为重要
- **可验证性**：形式化框架提供压缩保真度的可验证保证
- **资源受限场景**：精确的承诺保留避免不必要的上下文保留，降低内存需求

## 承诺类型

| 承诺类型 | 描述 | 压缩敏感度 |
|---------|------|----------|
| 目标承诺 | 任务目标、预期结果 | 高 |
| 约束承诺 | 硬约束、规则边界 | 高 |
| 决策承诺 | 已做决策及理由 | 中 |
| 偏好承诺 | 用户偏好、系统设置 | 中 |
| 工具承诺 | API 结果、检索内容 | 低 |

## 参考文献

（参考文献待从原文补充）
