---
title: "MemRouter: Memory-as-Embedding Routing for Long-Term Conversational Agents"
arXiv: 2605.00356
date: 2026-05-04
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Tianyu Hu, Weikai Lin, Weizhi Zhang, Jing Ma, Song Wang
- **提交日期**: 2026-05-04

## 摘要

Long-term conversational agents must decide which turns to store in external memory, yet recent systems rely on autoregressive LLM generation at every turn to make that decision—expensive and slow. MemRouter proposes a lightweight embedding-based router that decides what to memorize without LLM generation. The key insight is to treat memory writing as a routing problem: given the current turn embedding, predict which memory cluster it belongs to or if it should create a new cluster. MemRouter uses a two-tower architecture—one encoder for the incoming turn and one for existing memory clusters—to compute relevance scores via cosine similarity. Turns exceeding a learned threshold are written to memory; others are discarded. This avoids LLM calls during the store decision entirely. Experiments show MemRouter reduces memory write latency by 10x while achieving comparable downstream task performance compared to LLM-based memory selection, making it suitable for real-time conversational agents on resource-constrained devices.

## 核心贡献

1. **无 LLM 调用的记忆写入决策**: 用轻量 embedding 路由器替代 LLM 生成判断，降低延迟 10 倍
2. **双塔架构**: 分别编码输入 turn 和已有记忆簇，通过 cosine similarity 计算相关性
3. **自适应阈值**: 学习决定哪些 turn 值得写入记忆，避免内存污染

## 为什么重要

解决了记忆系统中最耗时的 LLM 调用问题——记忆写入决策无需 LLM 生成，使得实时对话 Agent 的记忆管理成为可能。

## 与端侧/移动端的相关性

**高度端侧相关**：MemRouter 核心创新在于用轻量 embedding 路由替代 LLM 调用，非常适合端侧/移动端部署。双塔编码器可使用小型 encoder 模型，在资源受限设备上运行流畅。
