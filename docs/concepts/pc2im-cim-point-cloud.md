---
type: concept
tags: [hardware, cim, point-cloud, mobile-perception, edge-computing, in-memory-computing]
related: [[edgecim-hardware-codesign]], [[rl-asic-exploration]], [[aeg-baremetal-ai-acceleration]]
sources:
  - url: https://arxiv.org/abs/2603.21167
    title: "PC2IM: An Efficient In-Memory Computing Accelerator for 3D Point Cloud"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# PC2IM: 面向移动端 3D 点云的存内计算加速器

> 一种 SRAM 存内计算（SRAM-CIM）加速器，专为资源受限的移动智能系统优化 3D 点云神经网络推理。

## 核心问题

3D 点云神经网络显著提升了移动端感知能力（自动驾驶、AR/VR、机器人导航），
但面临两个关键瓶颈：

1. **数据预处理的大量内存访问**: 点云数据的非结构化特性导致频繁的内存读写
2. **特征计算的高工作量**: PointNet/PointNet++ 等网络的特征提取层计算密集

这两个问题导致高能耗和高延迟，在电池供电的移动设备上尤为严重。

## 方法：SRAM-CIM 加速

PC2IM 采用 SRAM 存内计算架构，将计算直接嵌入存储单元：
- 消除数据在存储和计算单元之间的搬运
- 针对点云操作的特点优化数据布局
- 在保证精度的前提下最大化能效

## 为什么重要

对于手机端 AIOS：
- 3D 感知是 AR/MR 应用的核心能力
- 存内计算是突破"内存墙"的前沿方向
- 点云处理在 LiDAR 手机（iPhone Pro 系列）上已有实际应用
- 专用加速器能效远超通用 GPU

## 关联
- [[edgecim-hardware-codesign]] — 边缘 CIM 硬件协同设计
- [[rl-asic-exploration]] — RL 驱动的 ASIC 设计空间探索
- [[aeg-baremetal-ai-acceleration]] — 裸机 AI 加速
