---
type: concept
tags: [edge-ai, medical, multimodal, transformer, agentic, energy-efficient, 模型]
related: [[multimodal-edge-pruning]], [[networking-energy-agentic]], [[sustainability-ondevice-intelligence]]
sources:
  - "[arXiv] Sense Less, Infer More: Agentic Multimodal Transformers for Edge Medical Intelligence"
created: 2026-04-14
---

# Sense Less, Infer More：Agent 驱动的边缘医疗智能

## 概念定义

"Sense Less, Infer More" 提出了一种基于 Agent 的多模态 Transformer 架构，用于边缘医疗监测。核心思想是：持续采集传感器数据（ECG、PPG、EMG、IMU）会快速耗尽可穿戴设备电量，因此应该让 Agent 决定"何时感知、何时推理"，减少不必要的数据采集。

## 关键创新

1. **Agent 级感知控制**：由 AI Agent 决定何时激活传感器，而非持续采集
2. **多模态融合**：同时处理心电、脉搏、肌电、惯性等多种信号
3. **能量感知设计**：在诊断精度和能耗之间动态权衡

## 为什么重要

这代表了端侧 AI 的一个重要范式转变——从"被动感知+推理"到"主动决策+选择性感知"。在手机/可穿戴设备上，能耗是核心约束，Agent 级的感知控制可以：
- 延长电池续航 2-5 倍
- 减少不必要的数据处理和存储
- 保持甚至提升诊断准确性

## 与手机端 AIOS 的关联

手机和可穿戴设备是健康监测的主要平台。"Sense Less, Infer More" 的 Agent 化感知控制理念，与 [[networking-energy-agentic]] 中 Agent 能耗优化的思路一脉相承。未来手机 AIOS 可以将这种能力作为系统级服务提供给健康类 App。

## 相关概念

- [[multimodal-edge-pruning]] — 多模态边缘推理剪枝
- [[networking-energy-agentic]] — Agent 推理能耗优化
- [[sustainability-ondevice-intelligence]] — 端侧智能可持续性
