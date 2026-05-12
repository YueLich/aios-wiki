---
title: "Shepherd: A Runtime Substrate Empowering Meta-Agents with a Formalized Execution Trace"
arXiv: 2605.10913
date: 2026-05-11
tags: [agent-memory, memory-representation, meta-agents, execution-trace]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Shepherd: A Runtime Substrate Empowering Meta-Agents with a Formalized Execution Trace
- **作者**: Simon Yu, Derek Chong, Ananjan Nandi, Dilara Soylu, Jiuding Sun
- **发表日期**: 2026-05-11
- **arXiv ID**: 2605.10913
- **方向**: Meta-Agent 运行时基础设施 / 记忆表示

## 摘要

Shepherd introduces a functional programming model that formalizes meta-agent operations on target agents as functions, with core operations mechanized in Lean. The system records every agent-environment interaction as a typed event in a **Git-like execution trace**, enabling any past state to be forked and replayed. Shepherd forks the agent process and its filesystem **5× faster than Docker**, achieving **>95% prompt-cache reuse** on replay.

三个应用场景：
1. **Runtime Intervention**: 实时监督器将 CooperBench 通过率从 28.8% 提升到 54.7%
2. **Counterfactual Meta-Optimization**: 分支探索在四个基准上超越基线最高 11 分，wall-clock 时间减少 58%
3. **Tree-RL Training**: 在选定 turn 分叉 rollouts，TerminalBench-2 从 34.2% 提升到 39.4%

## 核心贡献

1. **Git-like Execution Trace**: 将每次 agent-environment 交互记录为 Lean 中的类型化事件，支持任意历史状态的 fork 和 replay
2. **高效 Fork 机制**: 比 Docker 快 5× 的进程 fork，>95% prompt-cache 复用率
3. **形式化语义**: 核心操作在 Lean 定理证明器中形式化，确保可验证性
4. **三大应用范式**: runtime intervention, counterfactual optimization, Tree-RL training

## 为什么重要

现有 meta-agent 系统缺乏可靠的运行时状态管理机制。Shepherd 通过引入 Git 式的执行轨迹，解决了：
- Agent 状态的持久化和回溯问题
- 分支探索的效率问题（相比 Docker 大幅提速）
- 运行时干预的可验证性问题

## 与移动端/端侧相关性

- 高效 fork 机制（5× Docker）对端侧资源受限环境有重要意义
- >95% prompt-cache 复用率可直接降低端侧推理成本
- Lean 形式化验证对安全关键型端侧 agent 部署有参考价值
