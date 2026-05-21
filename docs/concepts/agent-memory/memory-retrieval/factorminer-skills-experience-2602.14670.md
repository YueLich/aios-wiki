---
title: FactorMiner: A Self-Evolving Agent with Skills and Experience Memory for Financial Alpha Discovery
arXiv: 2602.14670
date: 2026-02-16
tags: ['agent-memory', 'memory-retrieval', 'experience-memory', 'financial-agent', 'self-evolving']
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **（核心贡献待从原文补充）**

## 方法

Formulaic alpha factor mining is a critical yet challenging task in quantitative investment, characterized by a vast search space and the need for domain-informed, interpretable signals. Finding novel signals becomes increasingly difficult as the library grows due to high redundancy.

The authors propose FactorMiner, a lightweight and flexible self-evolving agent framework designed for continuous knowledge accumulation. FactorMiner combines a Modular Skill Architecture that encapsulates systematic financial evaluation into executable tools with a structured Experience Memory that distills historical mining trials into actionable insights (successful patterns and failure constraints).

By instantiating the Ralph Loop paradigm — retrieve, generate, evaluate, and distill — FactorMiner iteratively uses memory priors to guide exploration, reducing redundant search while focusing on promising directions.

Experiments on multiple datasets across different assets and markets show that FactorMiner constructs a diverse library of high-quality factors with competitive performance while maintaining low redundancy among factors as the library scales.

## 为什么重要

本文提出了针对特定场景的 Agent 记忆系统设计。相比于将所有历史信息塞入上下文的简单方案，所提出的层次化/索引化经验记忆机制能够更高效地利用历史信息，同时支持跨任务的知识迁移。

## 与移动端/端侧的相关性

移动端 GUI Agent 需要在有限上下文窗口内处理长时程任务，经验记忆的压缩与索引机制对端侧部署具有重要意义。

## 参考文献

参考文献待从原文补充。
