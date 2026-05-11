---
title: "Knowledge-Graph Paths as Intermediate Supervision for Self-Evolving Search Agents"
arXiv: "2605.05702"
date: "2026-05-07"
tags: [agent-memory, memory-retrieval, knowledge-graph, search-agent, self-evolution]
reviewer: auto
source: arXiv API
---

## 摘要

Self-evolving search agents reduce reliance on human-written training questions by generating and solving their own search tasks. We build on Search Self-Play (SSP), a representative Proposer and Solver framework in which questions are generated and answered via multi-step search and reasoning. In practice, SSP faces two bottlenecks:

1. **Proposer 瓶颈**：从孤立答案实体构建问题，缺乏关系上下文，早期 self-play 训练产生大量无效/不可验证的问题
2. **Solver 瓶颈**：只接收二元结果奖励（binary outcome reward），丢弃来自部分正确搜索轨迹的有用信号

## 核心贡献

1. **KG 路径作为中间监督**：将知识图谱路径作为问题构建的 relation context，为 Proposer 提供关系上下文

2. **Waypoint Coverage Reward (WCR)**：为 Solver 提供分级部分信用（graded partial credit），根据其对构造路径上实体的覆盖情况进行奖励，而非简单的二元对/错

3. **知识复用**：问题构建和解答可以共享重叠的中间实体——构建问题时的 factual bridges 可作为解答问题的近似 waypoints

## 方法细节

### 问题构建的 KG grounding
- LLM-guided KG subgraph extraction 提供关系上下文
- Proposer 基于 KG 子图构建问题，而非孤立实体

### Waypoint Coverage Reward (WCR)
- 观察到：构造多跳问题和解答问题涉及重叠的中间实体
- 利用这种重叠：WCR 授予不正确轨迹部分信用，基于其对构造路径上实体的覆盖
- 正确轨迹仍获得全奖励

## 为什么重要

这篇论文对 Agent 记忆系统有重要启发：

1. **KG 路径作为结构化记忆检索结果**：Agent 在记忆检索后得到的路径，可以作为后续推理的中间步骤
2. **过程奖励（process reward）而非结果奖励（outcome reward）**：记忆系统应该能够评估"接近正确的轨迹"，而非仅判断最终答案
3. **自演化 Agent 的记忆积累**：随着 Agent 演化，其记忆系统应该从无效路径中学习（类似 WCR 的机制）

## 实验结果

在 7 个 QA 基准和 9 个模型配置上，平均分数在所有配置上都优于标准 SSP，在多跳 QA 任务上提升尤其显著。结果表明 KG 路径可作为轻量级中间监督，无需额外任务特定人工标注或手动标注的过程步骤。

## 与移动端/端侧相关性

- 端侧搜索/导航 Agent 可利用本地 KG 路径作为记忆检索的中间表示
- WCR 机制可用于评估端侧 Agent 的部分正确性，对用户体验很重要
- 轻量 KG 路径可存储在端侧，供离线使用

## 参考文献
