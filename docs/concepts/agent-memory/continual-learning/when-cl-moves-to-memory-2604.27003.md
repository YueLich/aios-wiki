---
title: "When Continual Learning Moves to Memory: A Study of Experience Reuse in LLM Agents"
arXiv: 2604.27003
date: 2026-04-29
authors: ["Qisheng Hu", "Quanyu Long", "Wenya Wang"]
tags: [agent-memory, continual-learning, memory-augmented-agents, context-window, experience-reuse]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.27003
- **作者**: Qisheng Hu, Quanyu Long, Wenya Wang
- **提交日期**: 2026-04-29
- **方向**: 记忆增强 Agent / 持续学习 / 经验复用

## 摘要（全文翻译）

记忆增强 LLM Agent 提供了一条诱人的捷径来实现持续学习：与其更新模型参数，不如将经验积累在外部记忆中，看似绕过了参数学习的稳定-可塑性困境。

本文展示了这个挑战**不会消失，只会在记忆层面重新出现**：在有限上下文窗口下，新旧经验在检索时竞争，记忆选择变得关键。

## 核心贡献

1. **记忆层面的稳定-可塑性困境**：将 CL 问题从参数层迁移到记忆层，并不解决根本问题
2. **上下文窗口竞争**：有限上下文下新旧经验的检索竞争
3. **经验复用策略分析**：系统研究 Agent 如何在外部记忆中复用经验

## 为什么重要

这是连接"参数 CL"和"记忆增强 Agent"两个领域的关键论文。核心发现：仅靠外部记忆无法实现真正的持续学习——稳定-可塑性困境只是换了一层重新出现。这对"记忆增强 = 持续学习"的 naive 理解是重要警示。

## 与端侧/移动端的相关性

端侧 Agent 特别容易遇到上下文窗口限制的问题。这篇论文的研究结论直接适用于移动端记忆系统的设计：不能简单认为"记忆够了就不用持续学习"。
