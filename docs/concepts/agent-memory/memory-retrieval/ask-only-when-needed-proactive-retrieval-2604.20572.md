---
title: "Ask Only When Needed: Proactive Retrieval from Memory and Skills for Experience-Driven Lifelong Agents"
arXiv: 2604.20572
date: 2026-04-15
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Yuxuan Cai, Jie Zhou, Qin Chen, Liang He
- **提交日期**: 2026-04-15

## 摘要

Online lifelong learning enables agents to accumulate experience across interactions and continually improve on long-horizon tasks. However, existing methods typically treat retrieval from past experiences as reactive—they retrieve after a task is given, not proactively anticipating what will be needed. This paper proposes proactive retrieval where the agent continuously maintains a "retrieval horizon"—a prediction of what task it will face next—based on its ongoing context. The agent updates retrieval proactively as its context evolves, so relevant memories are already loaded when needed. If the prediction is wrong, the agent falls back to reactive retrieval. This reduces average task completion latency by anticipating information needs.

## 核心贡献

1. **主动检索范式**: 预测下一个任务类型，提前加载相关记忆
2. **检索地平线维护**: 基于当前上下文持续更新未来任务预测
3. **预测失败回退**: 预测错误时回退到反应式检索，保证正确性

## 为什么重要

改变了记忆检索从被动到主动的根本范式，对于lifelong learning 场景可以显著降低任务完成延迟。

## 与端侧/移动端的相关性

**高度端侧相关**：减少反应式检索的 LLM 调用次数，对资源受限设备特别有价值。轻量任务预测模型可在端侧高效运行。
