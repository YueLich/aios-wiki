---
title: Human-Inspired Context-Selective Multimodal Memory for Social Robots
arXiv: 2604.12081
date: 2026-04-13
tags: [agent-memory, multimodal_memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.12081
- **作者**: Hangyeol Kang, Slava Voloshynovskiy, Nadia Magnenat Thalmann
- **提交日期**: 2026-04-13

## 摘要

Memory is fundamental to social interaction, enabling humans to recall meaningful past experiences and adapt their behavior accordingly based on the context. However, most current social robots and embodied agents rely on non-selective, text-based memory, limiting their ability to support personalized, context-aware interactions.

Drawing inspiration from cognitive neuroscience, we propose a context-selective, multimodal memory architecture for social robots that captures and retrieves both textual and visual episodic traces, prioritizing moments characterized by high emotional salience or scene distinctiveness.

The architecture mimics the human medial temporal lobe memory system: a fast-binding hippocampus-like module that rapidly encodes novel multimodal episodes, and a slow-consolidating neocortical module that extracts generalizable patterns over time. Context cues act as retrieval keys that selectively activate relevant episodic traces.

We implement this on a social robot platform and evaluate in human-robot interaction scenarios. The context-selective mechanism enables the robot to recall past interactions relevant to the current context while suppressing irrelevant memories, improving perceived personalization and interaction quality. Notably, the system gracefully handles the efficiency-accuracy tradeoff through adaptive allocation of memory resources based on contextual relevance.

## 核心贡献

1. **问题定义**: Human-Inspired Context-Selective Multimodal Memory for Social Robots 针对 multimodal memory 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 multimodal、memory 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
