---
title: "MemCoE: Learning How and What to Memorize — Cognition-Inspired Two-Stage Optimization for Evolving Memory"
arXiv: 2605.00702
date: 2026-05-01
authors: ["Derong Xu", "Shuochen Liu", "Pengfei Luo", "Pengyue Jia", "Yingyi Zhang", "Yi Wen", "Yimin Deng", "Wenlin Zhang", "Enhong Chen", "Xiangyu Zhao", "Tong Xu"]
tags: [agent-memory, memory-compression, continual-learning, cognition-inspired, preference-memory]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2605.00702
- **作者**: Derong Xu et al.
- **提交日期**: 2026-05-01
- **方向**: 记忆优化 / 持续学习 / 认知启发的记忆组织

## 摘要（全文翻译）

LLM Agent 需要长期用户记忆以实现一致的个性化，但有限的上下文窗口阻碍了长期交互中进化偏好的追踪。现有的记忆系统主要依赖静态、手工制定的更新规则；虽然基于强化学习（RL）的 Agent 学习记忆更新，但稀疏的结果奖励提供弱监督，导致不稳定的长期优化。

本文受**记忆 schema 理论**和**前额叶区域与海马体区域之间的功能分工**启发，提出 **MemCoE**，一个认知启发的两阶段优化框架，学习记忆应该如何组织以及应该更新什么信息。

第一阶段提出**记忆指南归纳（Memory Guideline Induction）**通过对比反馈优化全局记忆指南；第二阶段基于第一阶段的指南学习高效、增量式的记忆更新。大量实验表明 MemCoE 在长期偏好追踪上显著优于现有方法。

## 核心贡献

1. **两阶段记忆优化**：第一阶段学习"记忆应该如何组织"（Memory Guideline），第二阶段学习"如何更新特定信息"
2. **认知启发**：借鉴前额叶（全局指南/工作记忆）和海马体（快速增量更新）的功能分工
3. **对比反馈**：用对比学习信号替代稀疏的 RL 奖励信号，解决长期优化不稳定问题
4. **长期偏好追踪**：在用户偏好随时间演化的场景中验证方法有效性

## 为什么重要

MemCoE 解决了记忆系统的**"如何组织 + 何时更新"**两个核心问题。现有的方法要么固定记忆结构（手工规则），要么缺乏有效的长期优化信号（RL sparse reward）。MemCoE 的两阶段设计将记忆优化分解为：

- **what to memorize**（哪些信息值得进入记忆）
- **how to organize**（记忆的全局结构是什么）

这比单一的记忆更新规则更符合认知科学中对记忆系统的理解。

## 与端侧/移动端的相关性

认知启发的前额叶-海马体分工对端侧记忆系统有重要启示：端侧可以用一个轻量级的"工作记忆指南"（类似前额叶功能）配合快速的增量更新（类似海马体），实现高效的个性化记忆而不需要每次都调用云端 LLM 做复杂的记忆评估。
