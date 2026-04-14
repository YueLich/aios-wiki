---
type: concept
tags: [quantization, kv-cache, on-device, llm, memory, optimization, 优化技术]
related: [[on-device-inference]], [[lcsb-finetuning-ondevice]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.04722v1
    title: "Don't Waste Bits! Adaptive KV-Cache Quantization for Lightweight On-Device LLMs"
    date: 2026-04
created: 2026-04-14
---

# Don't Waste Bits! Adaptive KV-Cache Quantization for Lightweight On-Device LLMs

## 核心问题

Large Language Models (LLMs) have achieved remarkable progress across reasoning, generation, and decision-making tasks, yet deploying them on mobile, embedded, and edge devices remains particularly challenging.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- On-device LLM inference is heavily constrained by the memory and bandwidth overhead of the key-value (KV) cache, which grows linearly with context length and often dominates decoding cost.
- Inspired by Huffman coding's principle of variable-length allocation, we propose adaptive KV-cache quantization, a learned policy that assigns bit-width proportional to token importance, minimizing expected memory and latency without sacrificing competitive accuracy.

## 实验结果

论文报告了以下主要实验结果：

- Our framework extracts lightweight token-level features, including token frequency, quality score, attention variance, and entropy-based uncertainty, and feeds them into a compact data-driven controller that dynamically selects KV precision from {2-bit, 4-bit, 8-bit, FP16} during decoding.
- This adaptive precision policy reduces KV memory footprint and latency while improving accuracy compared to static KV quantization and rule-based baselines, and maintaining competitive accuracy close to FP16 inference across standard LLM benchmarks.
- Extensive experiments across multiple commonsense reasoning benchmarks using SmolLM-135M, SmolLM-360M, and SmolLM-1.7B demonstrate that our controller consistently improves the accuracy-latency trade-off.

## 为什么重要

该研究的重要性体现在：

- For instance, with SmolLM-360M on HellaSwag, our method reduces decoding latency (ms/token) by 17.75% relative to static KV quantization, improves accuracy by 7.60 points, and remains within only 0.30 points of FP16 inference.

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [on-device-inference

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.04722