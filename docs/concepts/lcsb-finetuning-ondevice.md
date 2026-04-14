---
type: concept
tags: [fine-tuning, on-device, memory-efficient, llm, layer-cyclic, 优化技术]
related: [[on-device-inference]], [[kv-cache-quantization-ondevice]], [[mobile-aios-overview]]
sources:
  - url: https://arxiv.org/abs/2602.13073v1
    title: "LCSB: Layer-Cyclic Selective Backpropagation for Memory-Efficient On-Device LLM Fine-Tuning"
    date: 2026-02
created: 2026-04-14
---

# LCSB：层循环选择性反向传播的端侧 LLM 内存高效微调

## 概述

LCSB 提出了一种内存高效的端侧 LLM 微调方法，通过层循环选择性反向传播来减少训练时的内存占用。

## 核心方法

传统微调需要存储所有层的激活值（用于反向传播），内存开销与层数成正比。LCSB 的创新：
- **层循环**：分批处理不同层的梯度计算
- **选择性反向传播**：只对关键层进行完整梯度计算
- **内存复用**：在不同层之间复用激活存储

## 为什么重要

端侧微调是 [[mobile-aios-overview]] 中「个性化 AI」的关键技术。用户希望模型能学习自己的使用习惯（参见 [[pspa-bench-gui-agent]] 的个性化评测），但微调的高内存需求一直是个障碍。LCSB 让在手机上进行增量微调成为可能。

## 关联

- [[kv-cache-quantization-ondevice]] — 推理阶段的内存优化
- [[on-device-inference]] — 端侧推理基础
- [[gui-agent-privacy]] — 本地微调保护隐私
