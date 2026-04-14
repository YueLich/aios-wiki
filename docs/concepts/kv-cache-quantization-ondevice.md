---
type: concept
tags: [quantization, kv-cache, on-device, llm, memory, optimization]
related: [[on-device-inference]], [[lcsb-finetuning-ondevice]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.04722v1
    title: "Don't Waste Bits! Adaptive KV-Cache Quantization for Lightweight On-Device LLMs"
    date: 2026-04
created: 2026-04-14
---

# 自适应 KV-Cache 量化：轻量级端侧 LLM 的内存优化

## 概述

这篇论文提出了一种自适应的 KV-Cache 量化方法，针对端侧轻量级 LLM 进行内存优化。KV-Cache 是 LLM 推理中存储历史键值对的缓存，随着上下文长度增长会占用大量内存。

## 核心问题

在 [[on-device-inference]] 场景中：
- 3B-7B 参数模型的 KV-Cache 在长上下文下可达数百 MB
- 手机 RAM 有限，KV-Cache 是内存瓶颈之一
- 传统均匀量化会损失过多精度

## 技术要点

- **自适应策略**：根据 token 重要性动态调整量化精度
- **轻量级模型优化**：专门针对 1B-3B 参数模型设计
- **质量保持**：在大幅减少内存占用的同时保持生成质量

## 为什么重要

KV-Cache 量化是延长端侧 LLM 上下文窗口的关键技术。与 [[lcsb-finetuning-ondevice]] 的内存高效微调配合，可以让手机运行更大上下文的 LLM 而不卡顿。

## 关联

- [[on-device-inference]] — 端侧推理基础
- [[mnn]]、[[llama.cpp]] — 推理引擎实现
- [[edgeflow-cold-start]] — 冷启动优化
