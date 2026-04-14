---
type: concept
tags: [hardware, cim, accelerator, edge, slm, co-design, 其他]
related: [[on-device-inference]], [[mobile-aios-overview]], [[edge-cloud-collaboration]]
sources:
  - url: https://arxiv.org/abs/2604.11512v1
    title: "EdgeCIM: A Hardware-Software Co-Design for CIM-Based Acceleration of Small Language Models"
    date: 2026-04
created: 2026-04-14
---

# EdgeCIM：基于 CIM 的小语言模型硬件-软件协同设计

## 概述

EdgeCIM 提出了一种用于加速小语言模型（SLM）的存内计算（CIM, Computing-In-Memory）硬件-软件协同设计方案。

## 核心概念

- **存内计算（CIM）**：直接在存储单元中执行矩阵运算，消除数据搬运开销
- **小语言模型（SLM）**：1-3B 参数量的模型，适合边缘部署
- **协同设计**：硬件架构和模型结构同步优化

## 为什么重要

这是 [[mobile-aios-overview]] 中「芯片层」的重要方向。当前端侧推理依赖通用 NPU（如 [[qualcomm]] 骁龙的 Hexagon），但 CIM 有潜力实现数量级的能效提升。长远来看，这可能改变手机芯片的设计范式。

## 关联

- [[on-device-inference]] — 端侧推理的硬件需求
- [[sustainability-ondevice-intelligence]] — 能效权衡
- [[edge-cloud-collaboration]] — 本地 vs 云端的硬件考量
