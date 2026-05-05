---
title: "Demonstrating Online Schema Alignment in Decentralized Knowledge Graphs Querying"
arXiv: 2604.19205
date: 2026-04-21
tags: [agent-memory, memory-representation, knowledge-graph]
reviewer: auto
source: arXiv RSS/API
---

# Demonstrating Online Schema Alignment in Decentralized Knowledge Graphs Querying

## 论文基本信息

- **作者**: Bryan-Elliott Tam, Pieter Colpaert, Ruben Taelman
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2604.19205
- **代码**: 公开可用（Comunica-based LTQP 引擎）

## 核心贡献

1. **在线模式对齐方法**: 提出针对链接遍历查询处理（LTQP）的在线模式对齐方法，在查询执行期间动态发现、作用域化和应用对齐规则。
2. **完整结果恢复**: 证明在线模式对齐可以低开销地恢复完整查询结果。
3. **实用基础**: 为 Web 规模 LTQP 系统推理提供了实用基础。

## 研究背景与问题

去中心化知识图谱查询支持集成分布式数据而无需集中化，但对词汇异质性高度敏感。查询发行者无法现实地预见所有词汇不匹配，尤其是当对齐规则是局部的、有作用域的或在运行时发现的时。

## 核心方法

**在线模式对齐**：

1. **动态发现**: 在查询执行期间动态发现对齐规则
2. **作用域化**: 对齐规则被限定在特定范围内
3. **动态应用**: 在查询执行过程中应用对齐规则，同时保持遍历行为

## 为什么重要

这篇 Demo 论文专注于去中心化知识图谱的查询问题，提出了运行时动态对齐方案。对 Agent 记忆系统在多源、分布式数据场景下的知识整合有参考意义。

## 与移动端/端侧相关性

端侧 Agent 可能需要从多个本地应用（日历、消息、邮件）整合信息——这本质上是小规模的去中心化知识图谱场景。动态模式对齐的思想可用于端侧记忆系统的多源数据融合。
