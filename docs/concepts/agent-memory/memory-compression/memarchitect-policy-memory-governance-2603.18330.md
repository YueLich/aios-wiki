---
title: "MemArchitect: A Policy Driven Memory Governance Layer"
arXiv: 2603.18330
date: 2026-03-23
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# MemArchitect: A Policy Driven Memory Governance Layer

## 论文基本信息

- **作者**: Lingavasan Suresh Kumar, Yang Ba, Rong Pan
- **arXiv**: https://arxiv.org/abs/2603.18330
- **领域**: cs.AI, cs.MA

## 摘要

持久化 LLM Agent 在记忆管理上面临关键治理缺口：标准 RAG 框架将记忆视为被动存储，缺乏解决矛盾、强制隐私或防止过时信息（"僵尸记忆"）污染上下文窗口的机制。MemArchitect 引入了一个治理层，将记忆管理从被动存储转变为主动治理。该层通过策略驱动的方式处理记忆的优先级、矛盾检测和隐私保护，确保 Agent 的上下文窗口始终由高质量、无矛盾的记忆组成。

## 核心贡献

1. **Memory Governance Layer**: 首个将记忆治理从被动存储提升为主动策略执行的框架
2. **Policy-driven Memory Management**: 用声明式策略（而非手工规则）定义记忆治理逻辑
3. **Contradiction Detection**: 自动检测记忆中的矛盾信息，并触发解决机制
4. **Zombie Memory Prevention**: 识别和标记过时记忆，防止其污染推理上下文
5. **Privacy Enforcement**: 策略驱动的隐私保护，自动删除或模糊化敏感记忆

## 研究背景与问题

标准 RAG 框架将记忆当作向量数据库——存储+检索，缺乏对记忆质量的主动管理。在实际部署中，Agent 记忆会积累过时信息、相互矛盾的信念和隐私敏感内容，但现有框架无法系统性地处理这些问题。

## 核心方法

1. **Governance Policy Language**: 设计声明式策略语言，定义记忆优先级、保留期、隐私级别
2. **Memory Contradiction Detector**: 时序推理引擎，检测记忆中相互矛盾的陈述
3. **Temporal Memory Tracker**: 追踪记忆的时间有效性，自动标记僵尸记忆
4. **Context Window Budget Allocator**: 根据策略为不同类型的记忆分配上下文预算
5. **Human-in-the-loop Override**: 支持人工干预策略执行，处理边界情况

## 为什么重要

MemArchitect 填补了 Agent 记忆系统从"存储"到"治理"的关键空白。RAG 只解决检索问题，MemArchitect 解决的是"什么记忆值得被检索"的问题。这是记忆系统从被动工具向主动智能体演进的核心能力。

## 与移动端/端侧相关性

1. **策略本地执行**: 治理策略可在端侧运行，无需云端协调
2. **隐私原生设计**: 敏感记忆不出设备，策略在本地强制执行
3. **资源感知治理**: 端侧存储受限时，策略可自动触发更激进的压缩/遗忘
4. **多 Agent 协调**: 分布式端侧多 Agent 系统中，共享治理策略确保记忆一致性
