---
title: "AtlasVA: Self-Evolving Visual Skill Memory for Teacher-Free VLM Agents"
arXiv: 2605.17933
date: 2026-05-18
tags: [multimodal-memory, visual-memory, VLM, self-evolution]
reviewer: auto
source: arXiv API
---

## 摘要

Vision-language model (VLM) agents increasingly rely on memory-augmented reinforcement learning to reuse experience across long-horizon tasks, yet most existing frameworks store memory as text and depend on proprietary teacher models to summarize or refine it. This design is poorly matched to spatial decision making: geometric priors are compressed into lossy language, and sparse interaction is often supervised through delayed textual feedback rather than dense visually grounded signals. We argue that reusable experience for VLM agents should remain visually grounded. Based on this insight, we propose \textbf{AtlasVA}, a teacher-free visual skill memory framework that organizes memory into three complementary layers: spatial heatmaps, visual exemplars, and symbolic text skills. AtlasVA further evolves danger and affinity atlases directly from trajectory statistics and lightweight grid heuristics, and reuses these self-evolving atlases as potential-based shaping rewards for reinforcement learning. This unifies perception, memory, and optimization without external LLM supervision. Experiments on \textsc{Sokoban}, \textsc{FrozenLake}, 3D embodied navigation, and 3D robotic manipulation benchmarks show that AtlasVA consistently outperforms text-centric memory baselines and competitive VLM agents, with especially strong gains on spatially intensive tasks. Homepage: https://wangpan-ustc.github.io/AtlasvaWeb

## 核心贡献

1. **提出Atlasva方法** — 针对现有记忆系统在任务泛化方面的不足
2. **关键设计** — 视觉技能记忆的自我进化机制，无需外部教师模型
3. **实验验证** — 在VLM代理任务上验证了方法的有效性

## 为什么重要

本文对于 Agent 记忆系统的研究具有重要意义：

- **长期记忆管理**：提出了无需教师模型的视觉技能记忆自我进化范式
- **实践价值**：降低了视觉技能记忆对人工标注的依赖

## 与端侧/移动端的相关性

视觉技能记忆可在边缘设备上本地化执行，支持离线VLM代理

## 参考文献

（参考文献待从原文补充）
