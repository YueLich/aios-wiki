---
title: "GSMem: 3D Gaussian Splatting as Persistent Spatial Memory for Zero-Shot Embodied Exploration and Reasoning"
arXiv: 2603.19137
date: 2026-03-19
tags: [agent-memory, multimodal-memory, embodied-ai, spatial-memory, 3dgs]
reviewer: auto
source: arXiv
---

## 论文基本信息

- **作者**: Yiren Lu, Yi Du, Disheng Liu, Yunlai Zhou, Chen Wang
- **发表**: 2026-03-19
- **类别**: cs.CV / cs.RO

## 摘要

有效的具身探索需要智能体随时间积累和保留空间知识。然而，现有场景表示（如离散场景图或静态视图快照）缺乏事后再观察性（post-hoc re-observability）：如果初始观察遗漏了目标由此产生的记忆缺失通常是不可恢复的。本文提出 GSMem——一个基于 3D Gaussian Splatting（3DGS）的零样本具身探索与推理框架。通过将连续几何和密集外观显式参数化，3DGS 作为持久空间记忆，使智能体具备空间回忆（Spatial Recollection）能力——即从最佳但先前未占据的视点渲染逼真新视图的能力。具体地，GSMem 采用并行目标级场景图和语义级语言场的双重检索机制，互补地定位目标区域，使智能体能够为高保真 VLM 推理"幻想"出最佳视图。此外，引入混合探索策略，平衡任务感知探索与几何覆盖。在具身问答和终身导航任务上的实验验证了框架的有效性和鲁棒性。

## 核心贡献

1. **3DGS 作为持久空间记忆**：将连续几何和外观参数化，实现 post-hoc re-observability
2. **空间回忆能力**：从先前未占据的最佳视点渲染逼真新视图
3. **双重检索机制**：结合目标级场景图和语义级语言场
4. **混合探索策略**：VLM 驱动的语义评分 + 3DGS 覆盖目标，平衡任务感知与几何探索
5. **零样本泛化**：无需任务特定训练即可在新环境中部署

## 为什么重要

突破了传统场景表示无法事后重新观察的局限，首次将 3DGS 引入具身智能体的持久记忆系统，为长期交互中的空间知识复用提供了新范式。

## 与移动端/端侧的相关性

3DGS 的计算量较大，当前主要面向高端设备。持久空间记忆对机器人等具身智能体的端侧部署具有重要意义，但 3DGS 的高效推理仍是开放问题。

---
*（参考文献待从原文补充）*
