---
title: "Dual-Cluster Memory Agent: Resolving Multi-Paradigm Ambiguity in Optimization Problem Solving"
arXiv: 2604.20183
date: 2026-04-22
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv API
---

# Dual-Cluster Memory Agent: Resolving Multi-Paradigm Ambiguity in Optimization Problem Solving

**作者:** Xinyu Zhang, Yuchen Wan, Boxuan Zhang, Zesheng Yang, Lingling Zhang, Bifan Wei, Jun Liu
**发表:** 2026-04-22

## 摘要

Large Language Models (LLMs) often struggle with structural ambiguity in optimization problems, where a single problem admits multiple related but conflicting modeling paradigms, hindering effective solution generation. To address this, we propose Dual-Cluster Memory Agent (DCM-Agent) to enhance performance by leveraging historical solutions in a training-free manner. Central to this is Dual-Cluster Memory Construction. This agent assigns historical solutions to modeling and coding clusters, then distills each cluster's content into three structured types: Approach, Checklist, and Pitfall. This process derives generalizable guidance knowledge. Furthermore, this agent introduces Memory-augmented Inference to dynamically navigate solution paths, detect and repair errors, and adaptively switch reasoning paths with structured knowledge.

## 核心贡献

1. **双簇记忆构造**: 将历史解法分配到建模簇和编码簇，蒸馏出 Approach、Checklist、Pitfall 三种结构化知识
2. **知识可迁移性发现**: 记忆由大模型构建可指导小模型获得更好性能，揭示了框架的 scalable efficiency
3. **记忆增强推理**: 动态导航解路径，检测并修复错误，自适应切换推理路径
4. **训练无关**: 完全依赖记忆和上下文，无需微调

## 实验结果

在 7 个优化基准上，DCM-Agent 取得 11%-21% 的平均性能提升。分析发现"知识继承"现象——大模型构建的记忆可以指导小模型获得更优性能。

## 为什么重要

首次系统研究了优化问题中的多范式歧义问题，并提出通过双簇记忆来区分和导航不同建模范式。这对于需要在不确定情况下生成高质量解决方案的 Agent 系统有直接价值。

## 与端侧/移动端的相关性

训练无关的特性使 DCM-Agent 特别适合端侧部署——可以直接复用云端构建的历史记忆，不需要端侧微调。知识蒸馏出的结构化知识（Approach/Checklist/Pitfall）紧凑且易于检索，对资源受限设备友好。
