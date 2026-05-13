---
title: "LongMemEval-V2: Evaluating Long-Term Agent Memory Toward Experienced Colleagues"
arXiv: 2605.12493
date: 2026-05-12
tags: [agent-memory, memory-retrieval, benchmark, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: LongMemEval-V2: Evaluating Long-Term Agent Memory Toward Experienced Colleagues
- **arXiv ID**: 2605.12493
- **发表日期**: 2026-05-12
- **作者**: Di Wu, Zixiang Ji, Asmi Kawatkar (Northeastern University, University of Michigan)
- **方向**: Agent Memory Benchmark / Memory Retrieval Evaluation
- **类别**: cs.CL, cs.AI

## 摘要

长期记忆对于专用 Web 环境中的智能体至关重要——成功取决于回忆界面功能、状态动态、工作流程和反复出现的失败模式。然而，现有的智能体记忆基准大多关注用户历史、短轨迹或下游任务成功，对记忆系统是否能有效内化环境特定经验缺乏直接评估。

本文提出 **LongMemEval-V2 (LME-V2)**，评估记忆系统是否能帮助智能体获取在定制环境中成为知识丰富同事的经验。LME-V2 包含 451 个手动策划的问题，覆盖 Web 智能体的五种核心记忆能力：静态状态回忆、动态状态跟踪、工作流知识、环境陷阱和前提意识。问题配对包含最多 500 条轨迹和 115M tokens 的历史轨迹。

论文提出两种记忆方法：**AgentRunbook-R**（基于 RAG 的高效记忆，含原始状态观测/事件/策略笔记知识池）和 **AgentRunbook-C**（将轨迹存为文件并调用编码智能体在增强沙箱中收集证据）。实验表明 AgentRunbook-C 以 72.5% 平均准确率超越最强 RAG 基线（48.5%）和现成编码智能体基线（69.3%）。

## 核心贡献

1. **LME-V2 基准**：451 个问题，5 类核心记忆能力，最多 115M tokens 历史轨迹
2. **AgentRunbook-R**：基于 RAG 的记忆系统，分层知识池（原始观测/事件/策略笔记）
3. **AgentRunbook-C**：轨迹编码 + 编码智能体沙箱证据收集，72.5% 平均准确率
4. **准确率-延迟 Pareto 前沿分析**：揭示记忆方法在精度与效率间的权衡

## 为什么重要

长期记忆是智能体在专业环境中真正"有经验"的核心能力。之前基准忽视了"智能体是否内化了环境特定经验"这一根本问题。LME-V2 填补了这一空白，推动记忆系统从"能检索"向"真正理解环境"的进化。

## 与移动端/端侧相关性

- 端侧 Web 智能体需要高效记忆系统，在有限资源下内化界面操作经验
- AgentRunbook-R 提供轻量级知识池方案，适合资源受限场景
- 记忆精度 vs 延迟的 Pareto 分析对端侧部署有直接指导价值

## 参考文献

- 原文: https://arxiv.org/abs/2605.12493
