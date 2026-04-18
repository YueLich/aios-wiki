---
type: concept
tags: [fine-tuning, on-device, memory-efficient, llm, layer-cyclic, 优化技术]
related: [[on-device-inference-memory-pressure]], [[kv-cache-quantization-ondevice]], [[mobile-aios-overview]]
sources:
  - url: https://arxiv.org/abs/2602.13073v1
    title: "LCSB: Layer-Cyclic Selective Backpropagation for Memory-Efficient On-Device LLM Fine-Tuning"
    date: 2026-02
created: 2026-04-14
---

# LCSB: Layer-Cyclic Selective Backpropagation for Memory-Efficient On-Device LLM Fine-Tuning

## 核心问题

Memory-efficient backpropagation (MeBP) has enabled first-order fine-tuning of large language models (LLMs) on mobile devices with less than 1GB memory.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- We propose Layer-Cyclic Selective Backpropagation (LCSB), which computes gradients for only a subset of layers per step.
- Our key insight is that residual connections guarantee gradient flow through identity paths, while AdamW momentum provides implicit updates for non-selected layers.

## 实验结果

论文报告了以下主要实验结果：

- We interpret LCSB as Block Coordinate Descent on the LoRA parameter space, providing theoretical justification for convergence.
- LCSB achieves up to 1.40$\times$ speedup with less than 2\% quality degradation across five models and three tasks.
- Surprisingly, in 4-bit quantized settings, LCSB exhibits superior stability: a 3B model that completely diverges under full backpropagation converges smoothly with LCSB, suggesting an implicit regularization effect from selective gradient computation.

## 为什么重要

该研究的重要性体现在：

- 提升了计算效率，使实际部署更加可行

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [on-device-inference

## 参考资源

- 论文原文：https://arxiv.org/abs/2602.13073