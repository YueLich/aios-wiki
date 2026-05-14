---
title: "IdeaForge: A Knowledge Graph-Grounded Multi-Agent Framework for Cross-Methodology Innovation Analysis and Patent Claim Generation"
arXiv: 2605.13311
date: 2026-05-13
tags: [agent-memory, knowledge-graph, multi-agent]
reviewer: auto
source: arXiv RSS/API
---

# IdeaForge: A Knowledge Graph-Grounded Multi-Agent Framework for Cross-Methodology Innovation Analysis and Patent Claim Generation

## 论文信息

- **arXiv ID**: 2605.13311
- **发表日期**: 2026-05-13
- **作者**: Joy Bose
- **类别**: cs.AI / cs.IR / cs.MA
- **链接**: https://arxiv.org/abs/2605.13311

## 摘要

当前 AI 辅助创新系统通常采用单一创意方法论（如 TRIZ 或设计思维），使用顺序化的基于提示的工作流，无法保留中间推理结构。因此跨方法论产生的洞察仍然碎片化，限制了可追溯性、综合性和新颖性评估的系统性。

本文提出 **IdeaForge**，一个基于知识图谱的多智能体框架，用于创新分析和专利权利要求生成。IdeaForge 通过操作持久化的 FalkorDB 知识图谱的专家智能体，整合多种创新方法论（TRIZ、设计思维和 SCAMPER）。每个智能体贡献代表矛盾、发明原理、用户需求、转化、类比和候选权利要求的结构化实体和关系。

IdeaForge 的核心贡献是通过基于图的**跨方法论收敛机制**实现的。独立被多种方法论支持的候选权利要求通过 CONVERGENT 关系连接，使得通过图遍历识别高置信度创新候选成为可能。下游专利起草智能体基于收敛权利要求子图生成结构化专利草案，减少对不受约束的语言模型生成的依赖。InnovationScore 公式根据收敛支持度、方法论多样性、权利要求强度和现有技术挑战计数对候选进行排名。

## 核心贡献

### 1. 跨方法论收敛机制
通过图连接的方式实现跨 TRIZ、设计思维、SCAMPER 方法论的知识整合，CONVERGENT 关系连接独立被多种方法论支持的候选权利要求。

### 2. 持久化知识图谱作为共享记忆
使用 FalkorDB 持久化知识图谱作为多智能体共享记忆存储，保留中间推理结构，支持专家智能体持续贡献结构化实体和关系。

### 3. 创新候选评估与排序
InnovationScore 公式综合考虑收敛支持度、方法论多样性、权利要求强度和现有技术挑战计数，为创新候选提供系统性排序。

### 4. 专利草案生成
下游专利起草智能体基于收敛的权利要求子图生成结构化专利草案，提高生成质量的可控性和可解释性。

## 为什么重要

本文解决了 AI 辅助创新系统中的碎片化问题。传统系统使用单一方法论且无法保留中间推理结构，限制了创新候选的可追溯性和综合评估能力。

IdeaForge 通过知识图谱作为持久化共享记忆，将多方法论产生的洞察统一存储，并通过图的遍历实现高置信度创新候选的识别。这一框架对需要整合多种推理方法的复杂 Agent 系统设计具有参考价值。

## 与移动端/端侧的相关性

- **知识图谱存储**：持久化图结构在端侧存储和查询有一定开销，但适合资源受限场景的增量更新
- **多智能体协作**：专家智能体通过共享知识图谱协作，适合分布式端侧部署场景
- **结构化输出**：通过知识图谱约束生成，提高输出可解释性，对端侧 Agent 的可信度有重要意义

## 参考文献

（参考文献待从原文补充）
