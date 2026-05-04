---
title: "Memanto: Typed Semantic Memory with Information-Theoretic Retrieval for Long-Horizon Agents"
arXiv: 2604.22085
date: 2026-04-23
authors: ["Seyed Moein Abtahi et al."]
tags: [agent-memory, memory-representation, typed-memory, information-theory, knowledge-graph-alternative]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.22085
- **作者**: Seyed Moein Abtahi, Rasa Rahnema, Hetkumar Patel et al.
- **提交日期**: 2026-04-23
- **方向**: 类型化语义记忆 / 信息论检索 / 长程 Agent

## 摘要（全文翻译）

从无状态语言模型推理到持久化多会话自主 Agent 的转变揭示了记忆成为生产级 Agent 系统部署的主要架构瓶颈。

现有方法主要依赖混合语义图架构，在摄取和检索阶段都产生大量计算开销——需要 LLM 介导的实体提取、显式图模式维护和多查询检索管道。

本文提出 **Memanto**，一个挑战"知识图谱复杂性是实现高保真 Agent 记忆的必要条件"这一流行假设的通用 Agent 记忆层。Memanto 集成了**13 种预定义记忆类别的类型化语义记忆模式**、自动冲突解决机制和时间版本控制。这些组件由 Moorcheh 的信息论搜索引擎启用。

## 核心贡献

1. **13 种预定义记忆类型**：超越简单的实体-关系图，用类型化的记忆模式捕获不同类别的经验
2. **无需 LLM 的信息论检索**：用 Moorcheh 引擎替代 LLM 介导的实体提取和检索，降低计算开销
3. **自动冲突解决**：同一事实的多个矛盾版本自动检测和解决
4. **时间版本控制**：记忆随时间演化，支持回溯到特定时间点的记忆状态

## 为什么重要

Memanto 挑战了"高保真 Agent 记忆 = 复杂知识图谱"的假设。通过类型化记忆和信息论检索，它用更简单的架构实现了高保真记忆，同时避免了 LLM 调用开销。这对端侧 Agent 特别有意义。

## 与端侧/移动端的相关性

Memanto 的"无 LLM 检索"设计对端侧部署极为友好。13 种预定义记忆类型覆盖了大多数 Agent 场景，设备端可以在不调用云端 LLM 的情况下维护和检索记忆。
