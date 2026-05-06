---
title: "When Modalities Remember: Continual Learning for Multimodal Knowledge Graphs"
arXiv: "2604.02778"
date: "2026-04-03"
tags: [agent-memory, continual-learning, multimodal-memory, knowledge-graph]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **首个持续多模态知识图谱推理（CMMKGR）系统研究**：填补了持续学习与多模态知识图谱推理的交叉空白。
2. **MRCKG 模型**：提出多模态-结构协作课程学习 + 跨模态知识保持 + 多模态对比回放的综合框架。
3. **基准数据集**：从现有 MMKG 数据集构建多个持续多模态知识图谱基准。
4. **跨模态知识保持机制**：通过实体表示稳定性、关系语义一致性、模态锚定三重机制缓解遗忘。

## 方法详解

### 问题背景
现实世界的多模态知识图谱（MMKG）是动态的，新实体、关系和多模态知识不断涌现。现有 CKGR 方法只关注结构三元组，无法充分利用新实体的多模态信号。现有 MMKGR 方法假设静态图，在图演化时遭受灾难性遗忘。

### MRCKG 方案
1. **Multimodal-Structural Collaborative Curriculum**：根据新三元组与历史图的拓扑连接性及其多模态兼容性调度渐进学习。
2. **Cross-Modal Knowledge Preservation**：通过三重机制（实体表示稳定性、关系语义一致性、模态锚定）保持跨模态知识。
3. **Multimodal Contrastive Replay**：两阶段优化策略，通过多模态重要性采样和表示对齐强化已学知识。

## 为什么重要

这是首个将持续学习扩展到多模态知识图谱的工作。传统 CKGR 只考虑结构+文本，但真实世界的知识图谱包含大量图像、音频等模态。多模态信号为新实体提供了额外的记忆线索，可以帮助区分新旧实体，从而缓解遗忘。

## 与端侧/移动端的相关性

**中等相关**。端侧 agent 通常需要在动态环境中持续学习新知识（新的物体、场景、用户偏好），多模态知识图谱是组织这些知识的自然方式。但当前研究主要面向服务器端 KG 推理，对资源受限设备的具体优化尚待探索。

## 摘要

Real-world multimodal knowledge graphs (MMKGs) are dynamic, with new entities, relations, and multimodal knowledge emerging over time. Existing continual knowledge graph reasoning (CKGR) methods focus on structural triples and cannot fully exploit multimodal signals from new entities. Existing multimodal knowledge graph reasoning (MMKGR) methods, however, usually assume static graphs and suffer catastrophic forgetting as graphs evolve. To address this gap, we present a systematic study of continual multimodal knowledge graph reasoning (CMMKGR). We construct several continual multimodal knowledge graph benchmarks from existing MMKG datasets and propose MRCKG, a new CMMKGR model. Specifically, MRCKG employs a multimodal-structural collaborative curriculum to schedule progressive learning based on the structural connectivity of new triples to the historical graph and their multimodal compatibility. It also introduces a cross-modal knowledge preservation mechanism to mitigate forgetting through entity representation stability, relational semantic consistency, and modality anchoring. In addition, a multimodal contrastive replay scheme with a two-stage optimization strategy reinforces learned knowledge via multimodal importance sampling and representation alignment. Experiments on multiple datasets show that MRCKG preserves previously learned multimodal knowledge while substantially improving the learning of new knowledge.

## 参考文献

- Linyu Li, Zhi Jin, Yichi Zhang, Dongming Jin, Yuanpeng He, Haoran Duan, Gadeng Luosang, Nyima Tashi. "When Modalities Remember: Continual Learning for Multimodal Knowledge Graphs." arXiv:2604.02778, 2026.
