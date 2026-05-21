---
title: OSGNet with MLLM Reranking @ Ego4D Episodic Memory Challenge 2026
arXiv: 2605.20818
date: 2026-05-20
tags: [agent-memory, memory-retrieval, multimodal]
reviewer: auto
source: arXiv RSS/API
---

# OSGNet with MLLM Reranking @ Ego4D Episodic Memory Challenge 2026

**arXiv**: 2605.20818 | **日期**: 2026-05-20 | **作者**: Yisen Feng, Leigang Qu, Haoyu Zhang, Qiaohui Chu

## 摘要

OSGNet with MLLM Reranking 是 CVPR 2026 Ego4D Episodic Memory Challenge 中 Natural Language Queries 和 GoalStep 两个赛道的冠军方案。该挑战要求从长未剪辑的第一人称视频中准确定位时间片段。方法采用基于重排序的框架，有效利用多模态大语言模型（MLLM）强大的视频-语言推理能力，同时保持传统定位流水线的高效性和候选召回。具体流程：首先从现有定位模型 OSGNet 获得候选片段集合，然后利用 MLLM 选择与给定查询最匹配的片段，从而精炼最终预测。方案最终在两个赛道均获第一。代码已开源。

## 核心贡献

1. **（参考文献待从原文补充）**

## 为什么重要

本文针对的是长程 Agent 的记忆系统关键挑战。与传统在离线场景设计的记忆方法不同，本文强调流式/在线视频理解中的实时记忆管理，对端侧 Agent 的实时视觉记忆有重要参考价值。

## 与端侧/移动端的相关性

- 视频流处理对端侧计算资源有严格限制，记忆压缩机制至关重要
- 轻量级视觉记忆管理对移动端/可穿戴设备上的视觉 Agent 有直接应用价值

## 参考文献

（参考文献待从原文补充）
