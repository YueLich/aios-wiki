---
title: "Beyond Position Bias: Shifting Context Compression from Position-Driven to Semantic-Driven"
arXiv: 2605.09463
date: 2026-05-10
tags: [agent-memory, memory-compression, context-compression]
reviewer: auto
source: arXiv API
---

## 核心贡献

本文提出 **SeCo**（Semantic Consistency Context Compression），将上下文压缩从「位置驱动」转变为「语义驱动」。核心问题：现有软提示压缩方法受限于位置偏差——依赖固定位置的可学习 token 插入或按物理 token 布局分组 token，导致性能不稳定和语义碎片化。

**SeCo 核心思路：**
- 不受物理 token 布局约束
- 以语义空间中的查询相关 token 为语义中心动态锚定压缩
- 通过一致性加权合并聚合剩余 token

## 为什么重要

长上下文场景中，LLM 面临高计算开销和信息冗余。现有压缩方法未能从根本上解决位置偏差问题。SeCo 通过语义驱动的压缩方式消除了这一根本性限制，在 14 个基准上持续表现优越。

## 与端侧/移动端相关性

- **下游任务性能优越**：14 个基准验证
- **推理延迟降低**：压缩后计算量减少
- **分布外泛化能力强**：跨领域鲁棒性验证
- **端侧友好**：更少 token = 更低内存和计算需求

## 方法论

### 语义中心选择
- 选择查询相关 token 作为语义中心
- 不依赖位置信息

### 一致性加权合并
- 剩余 token 通过一致性加权合并聚合至语义中心
- 保留语义一致性，消除位置偏差

## 实验结果

- 14 个基准 × 2 个骨干模型
- 下游任务持续优越
- 推理延迟改善
- 分布外鲁棒性验证

## 参考文献

（参考文献待从原文补充）
