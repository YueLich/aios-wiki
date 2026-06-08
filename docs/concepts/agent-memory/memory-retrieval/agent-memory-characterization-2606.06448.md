---
title: "Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads"
arXiv: 2606.06448
date: 2026-06-04
tags: [agent-memory, memory-retrieval, systems]
reviewer: auto
source: arXiv
---

# Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads

## 论文基本信息

- **作者**: Yasmine Omri, Ziyu Gan, Zachary Broveak, Robin Geens, Zexue He, Alex Pentland, Marian Verhelst, Tsachy Weissman, Thierry Tambe
- **提交日期**: 2026-06-04
- **分类**: cs.AI
- **arXiv ID**: 2606.06448

## 摘要

LLM agents are increasingly deployed on long-horizon tasks requiring sustained reasoning over extended interaction histories. Realizing this at scale requires agents to persistently store, retrieve, and update their own memory across sessions. A rich ecosystem of agent memory systems has emerged spanning flat retrieval, LLM-mediated extraction, consolidating fact stores, and agentic control flows. Yet, their system-level behavior remains uncharacterized. We present the first systems characterization of agent memory. First, we introduce a system-oriented taxonomy classifying agent memory systems along four axes. Second, we build a phase-aware profiling harness attributing cost to construction, retrieval, and generation. Third, we characterize ten representative systems across two benchmark suites, uncovering how design choices shift cost across the write and read paths. Finally, we derive 10 system recommendations covering construction scheduling, capability floors, amortization via query volume, freshness-latency tradeoffs, and fleet-scale management.

## 核心贡献

1. **四轴分类法 (Four-Axis Taxonomy)**: 首个从系统角度对 Agent Memory 系统进行分类的框架，沿四个轴对记忆系统进行分类：Memory construction（记忆构建）路径、Memory retrieval（记忆检索）路径、Memory update（记忆更新）策略、Memory control flow（记忆控制流）

2. **Phase-aware Profiling Harness**: 构建了一个能够将成本归因于构建(Construction)、检索(Retrieval)和生成(Generation)阶段的评测框架

3. **10系统实证分析**: 跨两个 benchmark 套件对 10 个代表性系统进行系统级表征，揭示设计选择如何影响写路径和读路径的成本分布

4. **10条系统建议**: 涵盖构建调度、能力下限、通过查询量摊销、新鲜度-延迟权衡以及fleet级管理

## 为什么重要

本文是首个从系统角度对 Agent Memory 进行全面表征的研究。随着 LLM Agent 在长期任务中的部署规模扩大，理解不同记忆系统在实际工作负载下的系统级行为变得至关重要。这项工作填补了从算法设计到系统优化的关键知识空白。

### 与移动端/端侧的相关性

1. **端侧部署的前提条件**: 论文指出外部记忆系统通过将状态持久化在外部并只检索查询相关子集，解决了上下文长度限制、KV-cache 内存压力和推理保真度下降三大约束——这些约束在资源受限的端侧设备上尤为突出

2. **写路径 vs 读路径权衡**: 论文揭示的设计选择对成本在读写路径间的分配影响，对端侧设备的资源预算分配有直接指导意义

3. **能力下限 (Capability Floors)**: 论文提出的系统建议有助于确定端侧记忆系统的最小能力要求

4. **新鲜度-延迟权衡**: 对需要实时更新的移动端应用（如个人助手、代码编辑器）有直接参考价值

## 核心内容解读

### 背景：为什么 Agent Memory 不同于传统 RAG

传统的 RAG 将知识与参数解耦，将 LLM 连接到静态外部语料库。而 Agent Memory 进一步扩展：记忆语料不再是预先处理和索引的固定文档集合，而是由智能体自身交互流产生的可变状态，通常按用户划分，可能在会话间追加、摘要、整合、链接或重写。

### 三种基础方案的局限性

1. **完整历史上下文**: 面临三个根本限制：上下文预算必然被超越、预填充成本随历史长度二次增长、推理和召回保真度在长序列中显著下降（"U形"性能曲线）

2. **外部记忆系统的核心价值**: 将容量与上下文长度解耦，绑定每次查询的预填充成本，使长时间域智能体执行可扩展

### 四轴分类法详解

论文提出的四轴分类：

- **Construction（构建）**: 如何从交互历史构建记忆（flat retrieval, LLM-mediated extraction, consolidating fact stores）
- **Retrieval（检索）**: 如何从记忆中检索相关内容（semantic search, structured query, learned retrieval）
- **Update（更新）**: 如何更新记忆（append-only, summarize, selective update）
- **Control Flow（控制流）**: 记忆如何影响 Agent 行为（agentic control flows）

### 10条系统建议（概述）

1. 记忆构建的调度策略
2. 能力下限的确定
3. 通过查询量摊销成本
4. 新鲜度与延迟的权衡
5. Fleet级管理建议

## 参考文献

（参考文献待从原文补充）
