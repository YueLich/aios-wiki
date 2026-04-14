---
type: concept
tags: [multimodal, pruning, edge, inference, optimization, zero-shot]
related: [[on-device-inference]], [[kv-cache-quantization-ondevice]], [[edgecim-hardware-codesign]]
sources:
  - url: https://arxiv.org/abs/2604.08971v1
    title: "Modality-Aware Zero-Shot Pruning and Sparse Attention for Efficient Multimodal Edge Inference"
    date: 2026-04
created: 2026-04-14
---

# 模态感知的零样本剪枝与稀疏注意力：高效的多模态边缘推理

## 概述

这篇论文提出了一种针对多模态模型的模态感知剪枝和稀疏注意力方法，用于提升边缘设备上的推理效率。

## 核心方法

- **模态感知剪枝**：根据不同模态（视觉、文本、音频）的特点进行差异化剪枝
- **零样本**：无需微调即可应用剪枝策略
- **稀疏注意力**：针对多模态 token 间的注意力模式进行优化

## 为什么重要

随着 [[gemma4-ondevice]] 等多模态模型在端侧部署，效率问题愈发突出。多模态模型的计算量远超纯文本模型，传统剪枝方法不考虑模态差异，效果有限。模态感知的方法能更精准地压缩模型。

## 关联

- [[on-device-inference]] — 端侧推理基础
- [[edgecim-hardware-codesign]] — 硬件加速协同
- [[kv-cache-quantization-ondevice]] — 内存优化
