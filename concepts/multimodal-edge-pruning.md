---
type: concept
tags: [multimodal, pruning, edge, inference, optimization, zero-shot, 优化技术]
related: [[on-device-inference]], [[kv-cache-quantization-ondevice]], [[edgecim-hardware-codesign]]
sources:
  - url: https://arxiv.org/abs/2604.08971v1
    title: "Modality-Aware Zero-Shot Pruning and Sparse Attention for Efficient Multimodal Edge Inference"
    date: 2026-04
created: 2026-04-14
---

# Modality-Aware Zero-Shot Pruning and Sparse Attention for Efficient Multimodal Edge Inference

## 核心问题

Edge devices increasingly run multimodal sensing pipelines that must remain accurate despite fluctuating power budgets and unpredictable sensor dropout.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- We present the SentryFuse framework, which addresses both challenges jointly through two key components.
- First, SentryGate learns modality-conditioned importance scores during training via first-order saliency supervision and then prunes attention heads and feed-forward channels at deployment without fine-tuning.

## 实验结果

论文报告了以下主要实验结果：

- Second, SentryAttend replaces dense self-attention, a key bottleneck in contemporary multimodal architectures, with sparse grouped-query attention, yielding a net 15% reduction in GFLOPs across three different multimodal architectures.
- Across three applications and multimodal backbones, SentryGate achieves a 12.7% average accuracy improvement over the strongest pruning baseline, and upto to 18% under modality dropout conditions.
- Together, SentryFuse reduces memory by 28.2% and lowers latency by up to $1.63\times$ without further fine-tuning, establishing modality-aware zero-shot compression as a practical path to multimodal intelligence on heterogeneous edge hardware.

## 为什么重要

该研究的重要性体现在：


## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [on-device-inference

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.08971