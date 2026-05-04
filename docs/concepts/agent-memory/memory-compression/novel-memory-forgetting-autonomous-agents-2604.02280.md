---
title: "Novel Memory Forgetting Techniques for Autonomous AI Agents: Balancing Relevance and Efficiency"
arXiv: 2604.02280
date: 2026-04-02
authors: ["Payal Fofadiya", "Sunil Tiwari"]
tags: [agent-memory, memory-compression, selective-forgetting, long-horizon-agents]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.02280
- **作者**: Payal Fofadiya, Sunil Tiwari
- **提交日期**: 2026-04-02
- **方向**: 记忆遗忘 / 长程 Agent / 上下文管理

## 摘要（全文翻译）

长期对话 Agent 需要持久记忆以保持连贯推理，但无控制的积累会导致**时间衰减**和**错误记忆传播**。LOCOMO 和 LOCCO 基准报告性能从 0.455 降至 0.05，MultiWOZ 在持续保留下显示 78.2% 准确率但有 6.8% 错误记忆率。

本文提出**自适应预算遗忘框架**，通过相关性引导评分和有界优化来调节记忆。方法整合**近因性、频率和语义对齐**来在约束上下文中保持稳定性。比较分析展示了改进的长程 F1 超过 0.583 基线水平，更高的保留一致性和减少的错误记忆行为，且不增加上下文使用。

## 核心贡献

1. **自适应预算遗忘框架**：在约束上下文预算下动态决定保留/遗忘哪些记忆
2. **三因素评分**：近因性（recency）+ 频率（frequency）+ 语义对齐（semantic alignment）
3. **有界优化**：确保遗忘决策在计算和存储约束内有理论保证
4. **实验验证**：在 LOCOMO、LOCCO、MultiWOZ 上验证长程 F1 和错误记忆率改善

## 为什么重要

这篇论文针对的是**长程 Agent 的记忆积累病态**——随着时间推移，记忆质量下降而非上升。核心洞察是遗忘不是简单的删除，而是**平衡探索和利用的优化问题**：保留太多导致噪声和错误记忆，遗忘太多损失有用的上下文信息。

## 与端侧/移动端的相关性

移动端 Agent 的上下文窗口极为有限，自适应预算遗忘框架对设备端记忆管理有直接参考价值。三因素评分（近因+频率+语义对齐）可以在端侧高效计算，不需要 LLM 参与遗忘决策。
