---
title: "A Survey of Spatial Memory Representations for Efficient Robot Navigation"
arXiv: 2604.16482
date: 2026-04-13
authors: ["Ma. Madecheen S. Pangaliman", "Steven S. Sison", "Erwin P. Quilloy", "Rowel Atienza"]
tags: [agent-memory, memory-representation, spatial-memory, robot-navigation, survey, edge-robotics]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.16482
- **作者**: Ma. Madecheen S. Pangaliman, Steven S. Sison, Erwin P. Quilloy, Rowel Atienza
- **提交日期**: 2026-04-13
- **方向**: 空间记忆 / 机器人导航 / 嵌入式系统 / 综述

## 摘要（全文翻译）

随着视觉机器人在更大环境中导航，它们的空间记忆无限增长，最终耗尽计算资源——尤其在嵌入式平台（8-16GB 共享内存，<30W）上，增加硬件不是选项。

本文调研了**空间记忆效率问题**，涵盖 88 篇参考文献、52 个系统（1989-2025），从占据栅格到神经隐式表示。

本文引入了 **α = M_peak / M_map**——运行时峰值内存与保存地图大小的比值。在 NVIDIA A100 GPU 上的独立分析显示，α 在纯神经方法内跨越两个数量级，从 2.3（Point-SLAM）到 215（NICE-SLAM，其 47MB 地图在运行时需要 10GB）。这表明**决定部署可行性的不是范式标签，而是记忆架构本身**。

## 核心贡献

1. **系统性调研**：1989-2025 年 52 个空间记忆系统的全面综述
2. **α 指标**：运行时峰值内存与持久化地图大小的比值，揭示"声称的地图大小"与"实际部署成本"的巨大差距
3. **嵌入式约束分析**：8-16GB/30W 嵌入式平台的空间记忆可行性评估
4. **范式对比**：占据栅格、特征地图、神经隐式等不同范式的内存效率对比

## 为什么重要

这是首个系统量化"地图存储大小 vs 实际运行时内存"差距的研究。核心发现：神经方法声称紧凑地图但运行时内存膨胀严重（α=215），而某些老方法反而更高效。这对嵌入式 Agent 的记忆系统设计有直接指导意义。

## 与端侧/移动端的相关性

**高度相关**。α 指标直接衡量了地图表示对嵌入式平台的适用性。移动机器人或 AR 设备的空间记忆系统必须同时考虑存储大小和运行时内存，而非仅看压缩率。
