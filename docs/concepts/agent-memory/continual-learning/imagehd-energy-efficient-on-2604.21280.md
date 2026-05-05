---
title: "ImageHD: Energy-Efficient On-Device Continual Learning of Visual Representations via Hyperdimensional Computing"
arXiv: 2604.21280
date: 2026-04-23
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# ImageHD: Energy-Efficient On-Device Continual Learning of Visual Representations via Hyperdimensional Computing

**作者:** Jebacyril Arockiaraj, Dhruv Parikh, Viktor Prasanna  
**发表:** 2026-04-23

## 摘要

On-device continual learning (CL) is critical for edge AI systems operating on non-stationary data streams, but most existing methods rely on backpropagation or exemplar-heavy classifiers, incurring substantial compute, memory, and latency overheads. Hyperdimensional computing (HDC) offers a lightweight alternative through fast, non-iterative online updates. Combined with a compact convolutional neural network (CNN) feature extractor, HDC enables efficient on-device adaptation with strong visual representations. However, prior HDC-based CL systems often depend on multi-tier memory hierarchies and complex cluster management, limiting deployability on resource-constrained hardware.
  We present ImageHD, an FPGA accelerator for on-device continual learning of visual data based on HDC. ImageHD targets streaming CL under strict latency and on-chip memory constraints, avoiding costly iterative optimization. At the algorithmic level, we introduce a hardware-aware CL method that bounds class exemplars through a unified exemplar memory and a hardware-efficient cluster merging strategy, while incorporating a quantized CNN front-end to reduce deployment overhead without sacrificing accuracy. At the system level, ImageHD is implemented as a streaming dataflow architecture on the AMD Zynq ZCU104 FPGA, integrating HDC encoding, similarity search, and bounded cluster management using word-packed binary hypervectors for massively parallel bitwise computation within tight on-chip resource budgets. On CORe50, ImageHD achieves up to 40.4x (4.84x) speedup and 383x (105.1x) energy efficiency over optimized CPU (GPU) baselines, demonstrating the practicality of HDC-enabled continual learning for real-time edge AI.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
