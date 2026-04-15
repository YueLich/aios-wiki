---
type: entity
tags: [arm, 推理框架, 计算库, mobile-inference, hardware-acceleration, sve]
related: [[edgecim-hardware-codesign]], [[rl-asic-exploration]], [[mnn-350]], [[ggml-llamacpp-hf]], [[sustainability-ondevice-intelligence]]
sources:
  - url: https://github.com/ARM-software/ComputeLibrary/releases/tag/v53.0.0
    title: "ARM Compute Library v53.0.0"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# ARM Compute Library v53.0.0

> ARM 官方 ML 推理计算库 v53.0.0 发布——新增 SVE TopKV 内核、实验性 FreeBSD 支持、多项稳定性修复。

## 概述

ARM Compute Library 是 ARM 官方的机器学习推理加速库，提供针对 ARM CPU 和 GPU 优化的 ML 算子实现。它是 MNN、TensorFlow Lite、PyTorch Mobile 等推理框架在 ARM 设备上的底层加速引擎。

## v53.0.0 主要更新

### 新功能
- **SVE TopKV 内核**：为 ARM SVE（Scalable Vector Extension）指令集添加 TopKV 算子内核。SVE 是 ARM 的下一代向量指令集，支持可变长度向量，在 Neoverse 服务器和高端移动端芯片上提供更好的 SIMD 利用率。
- **实验性 FreeBSD 支持**：首次支持 FreeBSD 操作系统，扩展了平台覆盖范围。
- **NETopKV 函数**：添加 Neon 指令集版本的 TopKV 实现。
- **验证函数支持左值**：改善 API 易用性。

### 破坏性变更
- 添加张量大小检查，防止超大张量输入。某些之前可工作的超大问题配置可能不再支持。

### 稳定性修复（12 项）
- CpuGemmConv2d 修复：不修改共享的 gemm_output_3d
- TopKV 比较中移除 epsilon
- GPU debug 构建错误修复
- Android NDK 构建修复：正确传递 --target 到汇编器
- NECropKernel 索引验证（production build 安全性）
- Im2Col 卷积 padding 修复
- CLMaxUnpoolingLayerKernel 索引检查

## 技术意义

### 对移动端 AI 推理的影响
1. **SVE 支持**：高端 ARM 芯片（Cortex-X 系列、Neoverse）越来越多支持 SVE。TopKV 内核是 RAG/Agent 场景中的关键操作（从大量候选中选择 top-k）。
2. **更稳定的 Android NDK 构建**：修复了 Android NDK 交叉编译中的 flag 传递问题，对 Android 推理框架集成更友好。
3. **张量大小安全检查**：防止 OOM 和未定义行为，对端侧内存受限环境尤为重要。

### 生态位置
```
应用层: 端侧 LLM App / AI Agent
框架层: MNN / TFLite / PyTorch Mobile
加速层: ARM Compute Library ← 本页
硬件层: ARM CPU/GPU (Cortex-A/X, Mali)
```

## 为什么重要

ARM Compute Library 是几乎所有在 ARM 设备上运行的 ML 推理框架的基础依赖。每次更新都影响着下游框架的性能和稳定性。v53.0.0 的 SVE 内核扩展意味着在支持 SVE 的设备上（如部分 Snapdragon、Exynos 芯片），TopK 操作（广泛用于采样、RAG 检索、Agent 决策）将获得硬件加速。

## 关联
- [[edgecim-hardware-codesign]] — EdgeCIM 做硬件协同设计，ARM Compute Library 是软件层实现
- [[rl-asic-exploration]] — RL 驱动 ASIC 探索，ARM Compute Library 定义了软件侧的算子需求
- [[mnn-350]] — MNN 3.5.0 使用 ARM Compute Library 作为底层加速
- [[ggml-llamacpp-hf]] — llama.cpp 有自己的 GGML 张量库，但部分场景也利用 ARM 优化
- [[sustainability-ondevice-intelligence]] — ARM Compute Library 的效率直接影响端侧推理的能耗
