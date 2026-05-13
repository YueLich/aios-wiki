---
title: "Executable Agentic Memory for GUI Agent"
arXiv: 2605.12294
date: 2026-05-12
tags: [agent-memory, memory-representation, knowledge-graph, GUI-automation]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Executable Agentic Memory (EAM): Executable Agentic Memory for GUI Agent
- **arXiv ID**: 2605.12294
- **发表日期**: 2026-05-12
- **作者**: Zerui Qin, Sheng Yue, Xingyuan Hua
- **方向**: Agent Memory Representation / Knowledge Graph for GUI
- **类别**: cs.AI

## 摘要

现代 GUI 智能体通常依赖模型中心化和逐步交互范式——LLM 必须在每个屏幕重新解释 UI 并重新决策动作，在长时域任务中脆弱不堪。

本文提出 **Executable Agentic Memory (EAM)**，一种结构化知识图谱（KG），将 GUI 规划从自由形式生成转向鲁棒的检索-执行过程。方法包括：
- **状态感知 DFS + 动作组挖掘**的样本高效记忆构建流水线，压缩多步例程
- **值引导图搜索**：轻量级 Q 函数模型引导 MCTS 在 KG 上搜索

论文在理论上建立了 Q 模型的一致性偏置，并推导了路径恢复的样本复杂度。实证上，EAM 在 AndroidWorld 上超越 UI-TARS-7B 达 19.6%，同时将 token 成本降低 6 倍，平均延迟仅 2.8 秒。

## 核心贡献

1. **EAM 架构**：将 GUI 记忆表示为可执行知识图谱，支持检索-执行范式
2. **状态感知 DFS + 动作组挖掘**：样本高效的记忆构建，从交互历史中自动提取多步例程
3. **值引导图搜索**：Q 函数引导 MCTS，平衡探索与利用
4. **理论保证**：bias-consistency 证明 + 路径恢复样本复杂度界

## 为什么重要

GUI 智能体的核心瓶颈在于"每步都重新理解 UI"的范式效率极低。EAM 通过将经验编码为可执行知识图谱，让智能体能够真正复用历史操作序列，而非每次从零开始。

## 与移动端/端侧相关性

- 端侧 GUI 自动化（如手机操作自动化）需要高效记忆系统存储 UI 操作模式
- 6 倍 token 成本降低 + 2.8s 低延迟，使其适合资源受限的移动设备
- MCTS + Q 函数的轻量搜索路径对端侧部署友好

## 参考文献

- 原文: https://arxiv.org/abs/2605.12294
