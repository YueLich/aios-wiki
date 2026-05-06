---
title: "Adaptive Data Compression and Reconstruction for Memory-Bounded EEG Continual Learning"
arXiv: 2605.03085
date: 2026-05-04
tags: [agent-memory, continual-learning, memory-compression]
reviewer: auto
source: arXiv API
---

# ADaCoRe: Adaptive Data Compression and Reconstruction for Memory-Bounded EEG Continual Learning

**作者:** Chengcheng Xie
**发表:** 2026-05-04

## 摘要

脑电图（EEG）信号提供毫秒级的时间分辨率，但其分析受到显著噪声和个体间差异的限制，在有限标注下难以实现稳健的个性化。已有研究提出无监督个体持续学习（UICL）来应对这一挑战：预训练模型需要在严格内存约束下适应未标记的个体数据流。然而，现有 UICL 方法通常存储完整的过去样本，违背了避免重训练的持续学习目标。

本文观察到 EEG 信号具有可利用的规则形态（well-structured morphologies），提出 **ADaCoRe（Adaptive Data Compression and Reconstruction）**，一种记忆高效的 UICL 流程，包含四个组件：

1. **显著性驱动关键帧保护（Saliency-driven Keyframe Protection）**: 选择性保护最重要的 EEG 形态
2. **有理多相压缩（Rational Polyphase Compression）**: 高效压缩 EEG 数据
3 **伴随重建与保护索引原样覆盖（Adjoint Reconstruction with Verbatim Overwrite）**: 保证重建质量
4. **原型置信度选择（Prototype-Confidence Selection）**: 自适应样本维护

在三个基准数据集上，ADaCoRe 在紧凑 buffer 条件下始终优于近期基线（在 ISRUC 和 FACED 数据集上分别提升至少 +2.7 和 +15.3 ACC）。

## 核心贡献

1. **记忆高效持续学习**: 首次针对 EEG 的无监督个体持续学习提出完整的数据压缩-重建 pipeline，在极小内存预算下保持模型性能
2. **形态感知压缩**: 利用 EEG 信号的规则形态进行压缩和重建，而非简单地下采样或存储原始数据
3. **显著性驱动的关键帧保护**: 区分重要和次要的 EEG 形态变化，优先保留关键信息
4. **原型置信度选择**: 提供自适应的样本维护策略，平衡存储效率和表示质量

## 为什么重要

可穿戴 EEG 设备（如消费级脑电头环）正在成为移动健康监测的重要工具。这类设备面临的挑战是：需要在边缘端持续学习用户的个体脑电特征（个性化），但存储和计算资源极度受限。

ADaCoRe 的意义在于：
- 提供了一种在 <1MB 内存预算下持续学习 EEG 的可行方案
- 揭示了形态感知压缩比通用压缩方法更适合生物信号
- 为其他时序信号的端侧持续学习提供了方法论参考

## 与端侧/移动端相关性

1. **可穿戴 EEG 设备**: 消费级脑电头环（如 Muse）需要在设备上持续学习用户脑电特征
2. **移动健康监测**: 移动端健康 App 需要在隐私保护前提下适应用户的个性化生理信号
3. **有限内存持续学习**: 移动端 AI 系统无法存储大量历史原始数据，必须在压缩表示上进行持续学习
4. **跨模态迁移**: ADaCoRe 的形态感知压缩方法可推广到其他生物信号（ECG、EMG）和时序传感器数据

**关键词**: EEG 持续学习、记忆压缩、自适应压缩重建、无监督个体学习、可穿戴设备、边缘 AI
