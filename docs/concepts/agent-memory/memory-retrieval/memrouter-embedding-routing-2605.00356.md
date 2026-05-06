---
title: "MemRouter: Memory-as-Embedding Routing for Long-Term Conversational Agents"
arXiv: 2605.00356
date: 2026-05-01
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

# MemRouter: Memory-as-Embedding Routing for Long-Term Conversational Agents

**作者:** Tianyu Hu, Weikai Lin, Weizhi Zhang, Jing Ma, Song Wang
**发表:** 2026-05-01

## 摘要

Long-term conversational agents must decide which turns to store in external memory, yet recent systems rely on autoregressive LLM generation at every turn to make that decision. We present MemRouter, a write-side memory router that decouples memory admission from the downstream answer backbone and replaces per-turn memory-management decoding with an embedding-based routing policy. MemRouter encodes each turn together with recent context, projects the resulting embeddings through a frozen LLM backbone, and predicts whether the turn should be stored using lightweight classification heads while training only 12M parameters.

## 核心贡献

1. **解耦记忆准入**: 将记忆管理与下游回答解耦，用 embedding 路由策略替代逐轮 LLM 生成决策
2. **极轻量参数**: 只训练 12M 参数的分类头，保持 LLM 主干冻结
3. **嵌入空间路由**: 将每个 turn 与近期上下文共同编码，通过冻结 LLM 主干投影后做路由判断
4. **延迟显著降低**: p50 记忆管理延迟从 970ms 降至 58ms（减少 94%）

## 实验结果

在 LoCoMo 上控制变量比较（检索 pipeline、答案提示和 QA 主干相同），MemRouter 在每个问题类别上均超越基于 LLM 的记忆管理器（总体 F1 52.0 vs 45.6）。因子分析显示：学习到的准入策略比随机存储提升 mean F1 +10.3，类别特定提示比通用提示提升 +5.2，检索贡献 +0.7。

## 为什么重要

解决了长期对话 Agent 中记忆管理的效率问题——不再需要每轮调用 LLM 做记忆决策，而是用轻量 embedding 路由替代。这对于需要高频交互的端侧 Agent 系统意义重大。

## 与端侧/移动端的相关性

**高度端侧相关**：仅 12M 可训练参数，延迟降低 94%，非常适合资源受限的移动设备。可以让端侧 Agent 在不显著增加计算负担的情况下实现智能记忆筛选。
