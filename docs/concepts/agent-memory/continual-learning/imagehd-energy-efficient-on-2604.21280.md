---
title: "ImageHD: Energy-Efficient On-Device Continual Learning of Visual Representations via Hyperdimensional Computing"
arXiv: 2604.21280
date: 2026-04-23
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# ImageHD: Energy-Efficient On-Device Continual Learning of Visual Representations via Hyperdimensional Computing

## 论文基本信息

- **作者**: Jebacyril Arockiaraj, Dhruv Parikh, Viktor Prasanna
- **arXiv**: https://arxiv.org/abs/2604.21280
- **领域**: cs.CV, cs.LG

## 摘要

端侧持续学习（CL）对在非平稳数据流上运行的边缘 AI 系统至关重要，但大多数现有方法依赖反向传播或需要大量样本的分类器，产生大量计算、内存和延迟开销。高维计算（HDC）通过快速、非迭代的在线更新提供了一种轻量级替代方案。结合紧凑卷积神经网络特征提取器，HDC 实现高效端侧适应与强视觉表示。然而，先前基于 HDC 的 CL 系统通常依赖多层内存层次。ImageHD 提出一种无需层级内存的高效端侧视觉表示持续学习框架。

## 核心贡献

1. **Hyperdimensional Computing CL**: 将 HDC 引入端侧持续视觉学习
2. **Energy-efficient Design**: 显著降低计算和内存开销
3. **No Multi-tier Memory**: 简化内存层次，适合资源受限端侧
4. **Non-iterative Online Updates**: 快速在线更新，无需迭代训练
5. **Visual Representation Learning**: 针对视觉表示的持续学习优化

## 研究背景与问题

端侧 CL 需要轻量级方法，但现有 HDC-based CL 系统依赖多层内存层次，增加了复杂度。ImageHD 简化了这一设计。

## 核心方法

1. **HDC-based Feature Encoding**: 使用高维向量编码视觉特征
2. **Fast Online Classifiers**: 基于 HDC 的快速在线分类器
3. **Single-tier Memory**: 无需多层内存层次的简化设计
4. **Energy-aware Updates**: 能耗感知的增量更新策略

## 为什么重要

ImageHD 展示了 HDC 在端侧持续学习中的潜力，对需要长时间独立运行的边缘 AI 系统有重要价值。轻量级在线更新对能耗受限的移动端设备尤为关键。

## 与移动端/端侧相关性

1. **超低能耗**: HDC 的非迭代更新极省能耗，适合物联网和可穿戴设备
2. **端侧持续学习**: 移动端视觉系统在非平稳数据流上的持续适应
3. **无层级内存**: 简化设计更适合资源极度受限的端侧设备
4. **实时更新**: 在线学习无需离线重训练
