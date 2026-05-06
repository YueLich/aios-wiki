---
title: "From Soliloquy to Agora: Memory-Enhanced LLM Agents with Decentralized Debate for Optimization Modeling"
arXiv: 2604.25847
date: 2026-04-28
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

# From Soliloquy to Agora: Memory-Enhanced LLM Agents with Decentralized Debate for Optimization Modeling

**作者:** Jianghao Lin, Zi Ling, Chenyu Zhou, Tianyi Xu, Ruoqing Jiang, Zizhuo Wang, Dongdong Ge
**发表:** 2026-04-28

## 摘要

Optimization modeling underpins real-world decision-making in logistics, manufacturing, energy, and public services, but reliably solving such problems from natural-language requirements remains challenging for current large language models (LLMs). In this paper, we propose Agora-Opt, a modular agentic framework for optimization modeling that combines decentralized debate with a read-write memory bank. Agora-Opt allows multiple agent teams to independently produce end-to-end solutions and reconcile them through an outcome-grounded debate protocol, while memory stores solver-verified artifacts and past disagreement resolutions to support training-free improvement over time.

## 核心贡献

1. **去中心化辩论协议**: 多 Agent 团队独立生成完整解决方案，通过基于结果的辩论协议协调
2. **读写记忆银行**: 存储 solver 验证过的 artifact 和历史分歧解决方案，支持免训练持续改进
3. **模块化框架**: 灵活适配不同骨干模型和方法，降低基础模型 lock-in，可跨 LLM 家族迁移
4. **无训练改进**: 辩论和记忆机制无需额外训练，可直接叠加到现有 pipeline

## 实验结果

在公共基准上，Agora-Opt 在所有比较方法中取得最强整体性能，超越了强 zero-shot LLMs、训练中心和 prior agentic 基线。分析显示跨骨干选择和组件变体均有稳健提升。

## 为什么重要

首次将辩论机制引入优化建模 Agent，并设计了读写记忆银行支持免训练的持续改进。去中心化辩论避免了单一 Agent 的盲点，记忆银行使每次辩论的成果得以积累复用。

## 与端侧/移动端的相关性

模块化设计允许在端侧部署轻量级版本——只保留记忆银行的核心检索功能，不需要完整的多 Agent 辩论。辩论协议本身可以作为安静模式运行，适合边缘服务器级别的优化任务。
