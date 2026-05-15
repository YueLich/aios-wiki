---
title: "Not All Memories Age the Same: Autodiscovery of Adaptive Decay in Knowledge Graphs"
arXiv: 2604.26970
date: 2026-04-22
tags: [agent-memory, memory-representation, knowledge-graph, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **作者**: Mandar Karhade
- **类别**: cs.IR (Information Retrieval)
- **发表**: 2026-04-22

## 摘要

现有知识图谱检索系统将所有事实视为同等时效性，应用均匀衰减曲线（uniform decay）处理时间信息。本文指出这一方法根本性错误：不同类型的知识表现出不同的时间动态特性，核心检索问题不是延迟或吞吐量，而是识别查询时什么知识是重要的。

本文提出层级框架，用**连续衰减表面**（continuous decay surface）替代均匀衰减，由两个正交信号参数化：
- **Velocity（速率）**：概念被观察到的频率
- **Volatility（波动性）**：观测值之间的变化程度（通过嵌入距离测量）

衰减表面分解为三个可学习层级：
1. **Domain-level**：捕捉通用模式（某些谓词天生永久，某些天生短暂）
2. **Context-level**：捕捉设置依赖的变化
3. **Entity-level**：针对特定主体个性化衰减

所有参数从数据中通过生存分析（survival analysis）涌现，无需预定义分类体系或领域专业知识。

## 核心贡献

1. **层次衰减表面**：将均匀衰减替换为 velocity-volatility 参数化的连续衰减表面
2. **生存分析方法**：将边生命周期形式化为生存问题，事件为值替代（supersession），而非简单重观测
3. **Lindy 效应验证**：velocity-volatility 聚类自然涌现，并与 Lindy 效应（Weibull shape k < 1）近乎普遍对齐
4. **实验验证**：合成时序知识图谱（HDBSCAN ARI = 1.0）、107 篇维基百科文章、1,163 条患者记录

## 为什么重要

现有知识图谱系统（如 RAG 架构中的知识存储）假设所有事实以相同速度过时，导致：
- 频繁变化的知识（新闻、股价）被低频更新
- 永久性知识（物理定律、历史事件）被不当过期

本文通过自适应衰减使知识图谱能够：
- 自动识别哪些知识是"永久性"的（Lindy 效应）
- 根据观察到的变化模式动态调整衰减速率
- 在检索时优先返回更可能准确的知识

## 与端侧/移动端的相关性

移动端 Agent 常面临知识快速过时的场景（位置信息、偏好变化、应用状态）。自适应衰减使端侧知识库能够：
- 根据使用频率自动调整知识重要性
- 减少过时知识的干扰
- 在有限存储中优先保留高价值记忆

## 参考文献

（参考文献待从原文补充）
