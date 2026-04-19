---
type: concept
tags: [NPU, LLM, test-time-scaling, inference-optimization, Qualcomm, Snapdragon, edge-ai, on-device]
related: [[edgedit]], [[minicpm-242]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2509.23324
    title: "Scaling LLM Test-Time Compute with Mobile NPU on Smartphones"
    date: 2025-09-27
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# 移动端 NPU 上的 LLM 测试时计算扩展

> 利用手机 NPU 中闲置的矩阵乘法算力，通过并行测试时扩展技术提升小型 LLM 的推理性能

## 核心问题

在移动设备上部署 LLM 面临两难困境：较小的模型性能不足，较大的模型资源消耗过大。研究发现，移动 NPU（特别是 Qualcomm Hexagon 的 HMX 矩阵乘法单元）在典型的 LLM 推理过程中存在大量**未被充分利用的计算资源**——每次矩阵乘法只使用了 HMX 的一小部分算力。

## 方法/架构

提出利用 NPU 闲置算力进行**并行测试时扩展**（parallel test-time scaling）的技术：

- **HMX 算力利用**：Hexagon NPU 包含 6-8 个标量 VLIW 硬件线程，向量运算由 HVX（Hexagon Vector eXtension）处理，矩阵运算由 HMX（Hexagon Matrix eXtension）处理。标准 LLM 推理仅使用了 HMX 的部分能力
- **并行测试时扩展**：在推理时生成多个候选回答并选择最佳结果，利用闲置的 HMX 算力并行执行
- **混合精度 GEMM 优化**：针对 Snapdragon 平台的 HMX 架构，实现了高效的混合精度矩阵乘法
- **Softmax 加速**：针对注意力机制中的 Softmax 操作进行 NPU 专用优化

## 实验结果

- **混合精度 GEMM**：最高 **19.0× 加速**
- **Softmax 操作**：最高 **2.2× 加速**
- 在 Gemma、Llama3.2、MiniCPM 等模型上验证
- **关键发现**：使用测试时扩展的小型模型可以**匹敌更大模型**的性能，同时充分利用 NPU 闲置算力
- 在 Qualcomm Snapdragon 平台上实现实际可用的推理速度

## 关键洞察

这篇论文揭示了一个被忽视的事实：**移动 NPU 的算力远未被充分利用**。传统的 LLM 推理流程（单次自回归生成）无法有效利用 HMX 的并行矩阵乘法能力。通过测试时扩展（多候选生成+选择），不仅提升了模型质量，还让 NPU 的算力"物尽其用"。

这对移动端 AI 部署的意义重大：不需要更大的模型，而是更聪明地利用现有硬件。

## 为什么重要

- **降低端侧 AI 成本**：小模型 + 测试时扩展 > 大模型，节省存储和功耗
- **推动 NPU 生态成熟**：现有 NPU SDK（QNN、Core ML）主要优化单模型推理，缺乏测试时扩展的支持
- **对小米/华为/三星的启示**：各自的 NPU 架构也存在类似的算力浪费问题，该方法可移植

## 关联
- [[edgedit]] — 另一个移动端 NPU 优化工作
- [[minicpm-242]] — 端侧小模型的代表
- [[on-device-inference-memory-pressure]] — 端侧推理的资源管理
- [[kv-cache-quantization-ondevice]] — 另一种端侧推理优化策略
