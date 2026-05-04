---
title: "Learning How and What to Memorize: Cognition-Inspired Two-Stage Optimization for Evolving Memory"
arXiv: 2605.00702
date: 2026-05-01
authors: "Multiple authors"
tags: [agent-memory, memory-evolution, preference-memory, reinforcement-learning]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2605.00702v1
- **发表**: 2026-05-01
- **作者**: 多个作者
- **方向**: 记忆演化 / 长期记忆优化
- **开源**: 待确认

---

## 问题背景

大型语言模型（LLM）Agent 需要长期用户记忆来实现一致的个性化，但有限的上下文窗口阻碍了长时间交互中用户演化偏好的追踪。现有的记忆系统主要依赖静态、手工设计的更新规则；虽然基于强化学习（RL）的 Agent 可以学习记忆更新，但稀疏的结果奖励提供弱监督，导致不稳定的长期优化。

---

## 核心贡献

本文提出 **MemCoE**（Memory Guideline Contrastive Optimization with Evolution），一个认知启发的两阶段优化框架：

1. **第一阶段：记忆指南归纳（Memory Guideline Induction）**
   - 通过对比反馈优化全局记忆指南，将文本梯度作为监督信号
   - 解决稀疏奖励问题

2. **第二阶段：指南对齐的记忆策略优化（Guideline-Aligned Memory Policy Optimization）**
   - 使用归纳的指南定义结构化过程奖励
   - 执行多轮 RL 学习指南跟随的记忆演化策略

---

## 为什么重要

本文将记忆 schema 理论与前额叶-海马体功能分工引入 LLM Agent 记忆系统，解决了：
- 长期偏好追踪中的上下文窗口限制
- 稀疏奖励导致的记忆更新不稳定
- 手工设计记忆更新规则缺乏适应性

---

## 与端侧/移动端的相关性

长期用户偏好记忆对移动端 Agent（手机助手、可穿戴 Agent）尤为重要。移动端场景下用户交互频率高、偏好演化快，需要轻量化且能适应用户习惯变化的记忆系统。MemCoE 的两阶段框架可迁移至端侧，在保持个性化服务质量的同时控制计算开销。

---

## 核心方法细节

### 记忆指南归纳

从用户反馈历史中归纳记忆优先级指南，使用对比学习区分高价值记忆与噪声记忆。

### 多轮强化学习

在多个记忆交互回合中执行 RL，让 Agent 学习何时更新记忆、更新什么内容，超越简单的阈值触发机制。

---

## 实验结果

在三个个性化记忆基准上评估，覆盖显式/隐式偏好、不同规模和噪声条件，相比强基线方法获得一致提升，且具有良好的：
- 鲁棒性
- 可迁移性
- 计算效率

---

## 相关工作对比

| 方法 | 记忆更新策略 | 偏好追踪 | 计算开销 |
|------|------------|---------|---------|
| MemCoE | RL+指南诱导 | 显式+隐式 | 中等 |
| 静态规则 | 手工阈值 | 仅显式 | 低 |
| 端到端RL | 端到端 | 隐式 | 高 |
