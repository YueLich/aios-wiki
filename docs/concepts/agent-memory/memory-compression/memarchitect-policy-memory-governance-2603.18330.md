---
title: "MemArchitect: A Policy Driven Memory Governance Layer"
arXiv: 2603.18330
date: 2026-03-18
tags: [agent-memory, memory-governance]
reviewer: auto
source: arXiv RSS/API
---

# MemArchitect: A Policy Driven Memory Governance Layer

## 论文基本信息

- **作者**: Lingavasan Suresh Kumar, Yang Ba, Rong Pan
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2603.18330
- **代码**: （待补充）

## 核心贡献

1. **治理层架构**: 提出 MemArchitect，将记忆生命周期管理与模型权重解耦的治理层。
2. **规则驱动策略**: 强制执行明确的规则，包括记忆衰减（memory decay）、冲突解决（conflict resolution）和隐私控制（privacy controls）。
3. **僵尸记忆防御**: 防止过时信息（"僵尸记忆"）污染上下文窗口。

## 研究背景与问题

持久化 LLM Agent 在记忆管理中存在关键治理缺口。标准 RAG 框架将记忆视为被动存储，缺乏：
- 解决矛盾的机制
- 隐私保护机制
- 防止过时信息（"zombie memories"）污染上下文窗口的机制

## 核心方法

**MemArchitect 治理层**：

1. **记忆衰减（Memory Decay）**: 自动衰减不再重要的记忆，防止记忆无限积累
2. **冲突解决（Conflict Resolution）**: 当新旧记忆矛盾时的解决策略
3. **隐私控制（Privacy Controls）**: 敏感信息的访问控制

**核心设计原则**: 将记忆生命周期管理与模型权重解耦——记忆的治理由外部规则系统负责，而非模型本身。

## 实验结果

在 Agentic 设置中，受治理的记忆一致性地优于无管理的记忆，突显了结构化记忆治理对可靠和安全的自主系统的必要性。

## 为什么重要

MemArchitect 提出了一个重要概念：记忆系统需要独立于模型的治理层。这对于构建可信赖的 Agent 系统至关重要——不仅仅是存储和检索，还需要主动管理记忆的质量、时效性和安全性。

## 与移动端/端侧相关性

端侧 Agent 需要在资源受限环境下自主运行，记忆的治理变得更加重要——没有云端监控的情况下，记忆衰减、冲突解决和隐私控制必须本地化执行。MemArchitect 的架构对端侧记忆治理系统有直接参考价值。
