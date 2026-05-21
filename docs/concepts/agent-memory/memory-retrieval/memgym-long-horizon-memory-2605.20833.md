---
title: "MemGym: a Long-Horizon Memory Environment for LLM Agents"
arXiv: "2605.20833"
date: "2026-05-20"
tags: [agent-memory, memory-retrieval, benchmark, evaluation]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: MemGym: a Long-Horizon Memory Environment for LLM Agents
- **arXiv ID**: 2605.20833
- **作者**: Wujiang Xu, Yu Wang, Kai Mei, Kaiqu Liang, Zhenting Wang, Mingyu Jin, Han Zhang, Shi-Xiong Zhang, Wenyue Hua, Sambit Sahu, Dimitris N. Metaxas
- **发表日期**: 2026-05-20
- **方向**: Agent Memory / Benchmark

## 核心贡献

1. **提出 MemGym 基准**: 首个针对 LLM Agent 长期任务中动态记忆形成的评估环境，统一了现有 Agent Gym 中的记忆评估维度。
2. **揭示现有基准缺陷**: 现有记忆基准主要评估多轮对话中的个性化信息保留，忽视了在代码编写、网页导航等真实 Agent 执行过程中发生的动态记忆构建。
3. **覆盖真实 Agent 场景**: MemGym 涵盖编码、Web 导航等扩展 Agent 执行场景，记忆系统在这些场景中的迁移能力与现有评估结果存在显著差异。

## 摘要

Memory is a central capability for LLM agents operating across long-horizon tasks. Existing memory benchmarks predominantly evaluate retention of personalized information in multi-turn chat scenarios, overlooking the dynamic memory formation that occurs during extended agent execution. Consequently, the memory systems they produce transfer poorly to realistic agentic environments, such as coding and web navigation. We present MemGym, a benchmark for agentic memory that unifies existing agent gym environments with memory-focused evaluation dimensions.

## 详细解读

### 研究背景

LLM Agent 在长期任务中需要持续积累和利用经验知识。现有记忆基准存在根本性局限：它们模拟的是聊天场景中的信息保留，而非真实 Agent 执行过程中的动态记忆构建。例如，一个代码生成 Agent 需要在调试过程中记住之前失败的尝试，一个网页导航 Agent 需要在多个页面跳转间维护状态认知。

### 核心方法

MemGym 的设计原则是让记忆评估贴近真实 Agent 执行：
- **动态记忆形成**: 评估 Agent 如何在执行过程中逐步构建和组织记忆
- **跨任务迁移**: 评估记忆系统在相似但不同的任务间的迁移能力
- **多维度评估**: 包括记忆的准确性、相关性、及时性和组织结构

### 实验发现

研究发现，在 MemGym 上的评估结果与现有基准存在显著差异，表明现有记忆系统的评估可能过于乐观，无法真实反映其在实际 Agent 场景中的表现。

## 为什么重要

Agent 记忆系统的发展长期受制于缺乏贴近真实场景的评估基准。MemGym 填补了这一空白，为 Agent 记忆系统的评估提供了更严格、更全面的标准，有助于推动记忆系统从实验室走向真实部署。

## 与端侧/移动端的相关性

虽然 MemGym 主要评估云端 LLM Agent，但长期记忆管理对移动端 Agent 同样重要。移动端 Agent 需要在资源受限环境下高效管理用户交互历史，本基准揭示的动态记忆形成机制可指导端侧记忆系统的设计，避免移动 Agent 在有限内存中堆积无用信息。

## 参考文献

（参考文献待从原文补充）
