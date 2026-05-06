---
title: "When Modalities Remember: Continual Learning for Multimodal Knowledge Graphs"
arXiv: "2604.02778"
date: "2026-04-03"
tags: [agent-memory, continual-learning, multimodal-memory, knowledge-graph]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

论文系统研究了**持续多模态知识图谱推理**（CMMKGR）问题——现实世界的多模态知识图谱（MMKGs）是动态的，新的实体、关系和多模态知识不断涌现。

**核心挑战**：
- 现有持续知识图谱推理（CKGR）方法只关注结构三元组，无法充分利用新实体的多模态信号
- 现有 MMKGR 方法假设图谱是静态的，在图谱演化时遭受灾难性遗忘

**论文贡献**：
1. 构建了首个持续多模态知识图谱推理的基准数据集
2. 提出了系统性研究框架 CMMKGR
3. 探索了如何在新实体出现时利用多模态信号（文本、图像等）来缓解遗忘

## 为什么重要

这是首个将持续学习扩展到多模态知识图谱的工作。传统 CKGR 只考虑结构+文本，但真实世界的知识图谱包含大量图像、音频等模态。多模态信号为新实体提供了额外的记忆线索，可以帮助区分新旧实体，从而缓解遗忘。

## 与端侧/移动端的相关性

**中等相关**。端侧 agent 通常需要在动态环境中持续学习新知识（新的物体、场景、用户偏好），多模态知识图谱是组织这些知识的自然方式。但当前研究主要面向服务器端KG推理，对资源受限设备的具体优化尚待探索。

## 摘要

Real-world multimodal knowledge graphs (MMKGs) are dynamic, with new entities, relations, and multimodal knowledge emerging over time. Existing continual knowledge graph reasoning (CKGR) methods focus on structural triples and cannot fully exploit multimodal signals from new entities. Existing multimodal knowledge graph reasoning (MMKGR) methods, however, usually assume static graphs and suffer catastrophic forgetting as graphs evolve. To address this gap, we present a systematic study of continual multimodal knowledge graph reasoning (CMMKGR).

## 参考文献

待补充
