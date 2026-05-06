---
title: "VimRAG: Navigating Massive Visual Context in Retrieval-Augmented Generation via Multimodal Memory Graph"
arXiv: 2602.12735
date: 2026-02-13
tags: [agent-memory, memory-retrieval, multimodal, visual-RAG, graph-memory]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Qiuchen Wang, Shihang Wang, Yu Zeng, Qiang Zhang, Fanrui Zhang (Alibaba-NLP)
- **提交日期**: 2026-02-13
- **方向**: 记忆检索 / 多模态RAG / 视觉记忆

## 摘要

传统RAG方法依赖线性交互历史，难以处理长上下文任务，尤其在涉及信息稀疏但token密集的视觉数据的迭代推理场景中表现尤为挣扎。为解决此问题，VimRAG提出了一种为文本、图像和视频的多模态检索增强推理而量身定制的框架。

核心思路：将推理过程建模为动态有向无环图（DAG），结构化组织Agent状态和检索到的多模态证据。在此结构化记忆基础上，引入**图调制的视觉记忆编码机制**——通过记忆节点在其图拓扑中的位置来评估其重要性，使模型能够动态为关键证据分配高分辨率token，同时压缩或丢弃无关线索。

## 核心贡献

1. **动态有向无环图记忆结构**：将Agent状态和检索到的多模态证据组织为DAG结构，突破线性历史的局限
2. **图调制视觉记忆编码（Graph-Modulated Visual Memory Encoding）**：根据节点拓扑位置评估记忆重要性，动态分配token预算
3. **图引导策略优化（Graph-Guided Policy Optimization）**：将逐步有效性与轨迹级奖励解耦，通过剪枝冗余动作对应的记忆节点实现细粒度信用分配
4. **SOTA性能**：在多种多模态RAG基准上均达到最优性能

## 方法详解

### 问题背景
传统RAG方法存在两个核心瓶颈：
- **线性历史限制**：按时间顺序存储交互历史，无法捕捉推理图中的多跳依赖关系
- **视觉token浪费**：图像/视频帧包含大量稀疏信息，全量编码导致token开销巨大

### 核心方法
1. **DAG结构化记忆**：将推理过程建模为有向无环图，每个节点代表一个推理步骤或一条检索到的证据，边代表逻辑依赖关系
2. **拓扑感知的重要性评分**：根据节点在图中的位置（如中间节点、汇聚节点）评估其信息价值
3. **动态token分配**：高重要性节点获得更多视觉token，低重要性节点被压缩或丢弃
4. **图引导优化**：通过策略梯度优化，在训练过程中学习如何剪枝冗余记忆

## 为什么重要

VimRAG将**图结构**引入多模态记忆检索，为处理海量视觉上下文提供了一种结构化的解决思路。对于端侧Agent而言，DAG结构比线性历史更高效——可以跳过无关的视觉帧，只检索与当前推理路径相关的节点，大幅降低计算和存储开销。

## 与其他方法对比

| 方法 | 记忆结构 | 视觉处理 | 适用场景 |
|------|---------|---------|---------|
| VimRAG | 动态DAG | 拓扑感知动态编码 | 长视频+多跳推理 |
| Mem0 | 向量数据库 | 全量编码 | 通用文本记忆 |
| RAG | 线性块 | 块级检索 | 短文本检索 |

## 参考文献

- VimRAG GitHub: https://github.com/Alibaba-NLP/VRAG
