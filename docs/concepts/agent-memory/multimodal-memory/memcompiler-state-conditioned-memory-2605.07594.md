---
title: "MemCompiler: Compile, Don't Inject — State-Conditioned Memory for Embodied Agents"
arXiv: 2605.07594
date: 2026-05-08
tags: [agent-memory, embodied-memory, memory-compilation]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

Existing memory systems for embodied agents typically inject retrieved memory as static context at episode start — a paradigm the authors call **Ahead-of-time Monolithic Memory Injection (AMMI)**. This static design becomes misaligned with the agent's evolving state and can degrade lightweight executors below the no-memory baseline. MemCompiler reframes memory utilization as State-Conditioned Memory Compilation: a learned Memory Compiler reads a structured Brief State capturing the agent's current execution state and dynamically selects and compiles only relevant memories at runtime.

## 核心贡献

1. **AMMI 范式的问题分析**：系统地分析了"静态记忆注入"范式在具身 Agent 中的根本性缺陷——记忆与 Agent 当前状态的对齐会随时间衰减
2. **状态条件记忆编译框架**：提出 MemCompiler，将记忆选择从"提前注入"转变为"运行时动态编译"
3. **Brief State 结构化表示**：设计了一种捕获 Agent 当前执行状态的结构化 Brief State，用于驱动记忆选择
4. **轻量级学习**：记忆编译器是可学习的，在保持执行器轻量的同时实现了记忆的动态适配

## 为什么重要

这是具身 Agent 记忆系统设计的一次重要范式转变。传统方法将记忆视为静态上下文，而 MemCompiler 将记忆视为根据当前状态动态编译的运行时资源。这种思路与"按需编译"而非"预加载"的计算哲学一致，对于需要长期运行的具身 Agent（如机器人、自动驾驶）特别重要。

## 与移动端/端侧相关性

端侧具身 Agent（机器人、无人机、自动驾驶车辆）是最典型的移动端 Agent 场景。MemCompiler 的轻量级动态记忆编译对资源受限的端侧设备特别有价值——它避免了为每一次执行预先加载完整记忆，而是根据当前状态按需编译，既节省了 token 预算，又保证了记忆与当前任务的对齐。

## 参考文献

- arXiv: https://arxiv.org/abs/2605.07594
- Authors: Xin Ding, Xinrui Wang, Yifan Yang
