---
title: "SAGE: A Self-Evolving Agentic Graph-Memory Engine for Structure-Aware Associative Memory"
arXiv: 2605.12061
date: 2026-05-12
tags: [agent-memory, memory-representation, graph-memory, self-evolving]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: SAGE: A Self-Evolving Agentic Graph-Memory Engine for Structure-Aware Associative Memory
- **arXiv ID**: 2605.12061
- **发表日期**: 2026-05-12
- **作者**: Juntong Wang, Haoyue Zhao, Guanghui Pan
- **方向**: Agent Memory Representation / Graph Memory
- **类别**: cs.AI

## 摘要

长期记忆正成为语言智能体的核心瓶颈。现有 RAG 和 GraphRAG 系统大多将记忆图作为静态检索中间件，限制了从部分线索恢复完整证据链、利用可复用图结构角色以及通过下游反馈改进记忆的能力。

本文提出 **SAGE**，一个自进化智能体图记忆引擎，将图记忆建模为动态长期记忆基质。SAGE 耦合两个角色：

- **记忆写入器**（Memory Writer）：从交互历史增量构建结构化图记忆
- **基于图基础模型的记忆读取器**（Graph Foundation Model-based Reader）：执行检索并向记忆写入器提供反馈

论文提供了严格的理论分析支持。在多跳 QA、开放域检索、领域特定评审 QA 和长期智能体记忆基准上的实验表明，SAGE 改善了证据恢复、答案支撑和检索效率。经过两轮自进化后，在多跳 QA 上达到最佳平均排名；在零样本开放域迁移中，在 NQ 上达到 82.5/91.6 Recall@2/5。LongMemEval 和 HaluMem 结果表明，训练和读写器反馈改善了多个长期记忆和幻觉诊断指标。

## 核心贡献

1. **SAGE 架构**：自进化图记忆引擎，动态耦合读写器
2. **图基础模型 Reader**：利用图的结构化表示进行关联记忆检索
3. **读写器反馈机制**：Reader 反馈改进 Writer，实现记忆自我进化
4. **理论分析**：框架的理论支撑，证明自进化的收敛性

## 为什么重要

现有记忆系统大多将"写入"和"读取"分离，忽视了两者协同进化的潜力。SAGE 打破了这一范式，让记忆系统能够从检索反馈中持续改进，实现真正的持续学习。

## 与移动端/端侧相关性

- 端侧智能体需要能够在本地持续改进的记忆系统
- 自进化机制减少了人工干预，适合长期运行的端侧应用
- 图基础模型的轻量化版本对端侧部署有参考价值

## 参考文献

- 原文: https://arxiv.org/abs/2605.12061
