---
title: "A Self-Evolving Framework for Efficient Terminal Agents via Observational Context Compression"
arXiv: 2604.19572
date: 2026-04-21
tags: [agent-memory, memory-compression, terminal-agents]
reviewer: auto
source: arXiv API
---

## 核心贡献

本文提出 **TACO**（Terminal Agent Compression），一个用于高效终端 Agent 的可插拔、训练无关、自进化的观测上下文压缩框架。核心解决：终端 Agent 在长时域多轮工作流中，交互历史积累大量噪声终端观测，导致上下文饱和和高 token 成本。

**关键创新点：**
- **自进化压缩规则**：从交互轨迹中自动发现、细化和复用结构化压缩规则
- **工作流自适应过滤**：根据工作流类型自适应过滤低价值终端输出，同时保留任务相关观测
- **无需训练**：直接应用于现有终端 Agent，无需额外训练

## 为什么重要

终端环境高度异构（不同仓库、命令、执行状态），传统启发式或固定压缩方法难以泛化。TACO 通过自进化方式自动适应不同工作流，在保持任务关键信号的同时压缩上下文。

## 与端侧/移动端相关性

- **Token 成本降低**：长时域任务中 token 消耗是主要成本，对边缘部署尤为重要
- **推理效率提升**：1%-4% 准确率提升 + 相同 token 预算下 2%-3% 额外提升
- **通用性强**：适用于多种 Agent 框架和骨干模型

## 实验验证

基准测试：TerminalBench（TB 1.0 和 TB 2.0）、SWE-Bench Lite、CompileBench、DevEval、CRUST-Bench

**主要结果：**
- TerminalBench：强 Agent 模型上 1%-4% 准确率提升
- 相同 token 预算下额外 2%-3% 准确率提升
- 额外基准：保持/提升任务成功率的同时降低总 token 消耗

## 方法细节

TACO 三阶段流程：
1. **规则发现**：从初始交互轨迹中识别压缩模式
2. **规则细化**：基于反馈持续优化压缩规则
3. **规则复用**：将学习到的规则应用于新任务

核心机制：结构化压缩规则 + 工作流感知过滤

## 参考文献

（参考文献待从原文补充）
