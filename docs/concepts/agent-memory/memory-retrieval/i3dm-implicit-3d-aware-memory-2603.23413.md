---
title: "I3DM: Implicit 3D-aware Memory Retrieval and Injection for Consistent Video Scene Generation"
arXiv: 2603.23413
date: 2026-03-24
authors: ["Jia Li", "Han Yan", "Yihang Chen", "Siqi Li", "Xibin Song", "Yifu Wang", "Jianfei Cai", "Tien-Tsin Wong", "Pan Ji"]
tags: [agent-memory, 3D-memory, video-generation, scene-consistency, embodied-ai, memory-retrieval]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2603.23413
- **发表日期**: 2026-03-24
- **作者**: Jia Li, Han Yan, Yihang Chen, Siqi Li, Xibin Song, Yifu Wang, Jianfei Cai, Tien-Tsin Wong, Pan Ji
- **方向**: 3D 感知记忆（视频生成中的隐式 3D 记忆检索）

## 摘要

**背景**：视频生成已取得显著进展，但重返先前探索区域时维持长期场景一致性仍具挑战。现有方案依赖显式 3D 几何构建（存在误差积累和尺度模糊问题）或朴素的 FoV 检索（复杂遮挡下失效）。

**方法**：I3DM 提出隐式 3D 感知记忆机制，无需显式 3D 重建即可实现一致的视频场景生成。核心是 3D 感知记忆检索策略——利用预训练前馈新视角合成（FF-NVS）模型的中间特征评分视角相关性，在高度遮挡场景下实现鲁棒检索。进一步引入 3D 对齐记忆注入模块，将历史内容隐式变形到目标视角，并自适应地基于可靠变形区域调节生成。

**实验结果**：在重返一致性、生成保真度和相机控制精度上均超越 SOTA 方法。

## 核心贡献

1. **隐式 3D 感知记忆**：绕过显式 3D 重建实现场景一致性，规避误差积累问题
2. **FF-NVS 特征检索**：利用预训练新视角合成模型的中间特征评分，避免传统 FoV 检索的遮挡失败问题
3. **3D 对齐记忆注入**：将历史帧变形到当前视角，自适应条件生成
4. **端到端视频生成**：从记忆检索到注入的完整 pipeline

## 为什么重要

场景一致性是视频生成的长期难题：

- **Agent 视觉记忆**：具身 Agent 视觉记忆需要在重返位置时保持一致性
- **3D 先验利用**：利用预训练 3D 先验而非显式重建，更鲁棒
- **遮挡处理**：这是 3D 记忆系统最难处理的情况，I3DM 通过 FF-NVS 中间特征解决了这一问题

## 与端侧/移动端的相关性

对端侧具身 Agent 有参考价值：

- **视觉记忆压缩**：3D 隐式表示比存储多视角图像更高效，适合移动端存储限制
- **边缘视频生成**：记忆检索+变形生成可在边缘设备上实现，无需云端处理
- **AR 场景一致性**：AR 设备重返位置时需要一致的虚拟物体叠加

## 参考文献

- arXiv: 2603.23413 | https://arxiv.org/abs/2603.23413
