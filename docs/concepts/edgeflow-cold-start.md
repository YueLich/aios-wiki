---
type: concept
tags: [inference, mobile, optimization, cold-start, llm, 优化技术]
related: [[on-device-inference-memory-pressure]], [[edge-cloud-offloading]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.09083v1
    title: "EdgeFlow: Fast Cold Starts for LLMs on Mobile Devices"
    date: 2026-04
created: 2026-04-14
---

# EdgeFlow: Fast Cold Starts for LLMs on Mobile Devices

## 核心问题

Deploying large language models (LLMs) on mobile devices is an emerging trend to enable data privacy and offline accessibility of LLM applications.

## 方法/架构

基于论文摘要，该方法包含以下关键创新点：

- Modern mobile neural processing units (NPUs) make such deployment increasingly feasible.
- In this paper, we identify the key bottleneck of mobile LLM cold starts as the waste of flash bandwidth on unimportant model parameters.

## 实验结果

论文报告了以下主要实验结果：

- We design EdgeFlow, a mobile LLM inference framework that mitigates the cold start issue by adaptively adjusting the precisions of LLM parameters.
- Specifically, EdgeFlow leverages 1) an NPU-aware adaptive quantization algorithm that assigns different precisions to weights in a finer granularity according to their importance and NPU constraints, 2) an SIMD-friendly packing format that accelerates the transformation of various-precision weights into fixed-sized NPU-native data types, and 3) a synergistic granular pipeline that coordinates CPU and NPU computation in a fine-grained and dynamic manner.
- Experimental results show that EdgeFlow reduces cold-start latency by up to 4.07x compared with three state-of-the-art mobile LLM inference frameworks, i.e., llama.cpp, MNN, and llm.npu, under comparable model accuracy.

## 为什么重要

该研究的重要性体现在：

- 关注隐私保护，符合数据安全趋势

## 关联

基于论文内容和研究领域，该工作与以下概念相关：

- [on-device-inference

## 参考资源

- 论文原文：https://arxiv.org/abs/2604.09083