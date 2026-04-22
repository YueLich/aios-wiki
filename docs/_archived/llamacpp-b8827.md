---
type: entity
tags: [推理框架, inference, opencl, adreno, qualcomm, gpu, llama-cpp]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[coremltools-9]], [[edgeflow-cold-start]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8827
    title: "ggml-org/llama.cpp: b8827"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# llama.cpp b8827

> OpenCL 后端重构 Adreno GPU 的 q8_0 量化矩阵运算调度，改善 Qualcomm 设备上的推理性能。

## 核心更新

本次发布的亮点是 PR #21938：**OpenCL q8_0 set_tensor 和 mul_mat 主机端调度重构**，专门针对 Adreno GPU（Qualcomm Snapdragon 系列）。

### 技术细节

- **q8_0 GEMM/GEMV Adreno 调度重构**：重新设计了 q8_0 量化格式在 Adreno GPU 上的矩阵乘法（GEMM）和矩阵向量乘法（GEMV）的主机端分发逻辑
- **set_tensor 优化**：改进了张量数据在 GPU 内存中的布局和传输方式
- **代码质量**：修复空白符问题，提升代码一致性

### 平台支持

b8827 继续提供全面的跨平台二进制分发：

| 平台 | 变体 |
|------|------|
| macOS | arm64, arm64 KleidiAI, x64 |
| iOS | XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan x64/arm64, ROCm 7.2, OpenVINO |
| Windows | x64/arm64 CPU, CUDA 12 |

## 为什么重要

对手机端 AIOS 生态而言：

- **Qualcomm Adreno 是 Android 主流 GPU**：几乎所有 Snapdragon 芯片都使用 Adreno GPU，此次重构直接影响数十亿 Android 设备的端侧推理性能
- **q8_0 是移动端常用量化格式**：相比 FP16 减半内存占用，同时保持较高精度，是端侧 LLM 推理的主力格式
- **OpenCL 是跨厂商 GPU 标准**：不依赖 Vulkan 或 CUDA，可在 Qualcomm/Mali/PowerVR 等多种移动 GPU 上运行
- **从 b8783 到 b8827 持续迭代**：44 个版本的快速迭代说明 llama.cpp 团队对移动端 GPU 支持的持续投入

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 母项目概述，本次更新是其 OpenCL 移动端能力的延续
- [[mnn-350]] — MNN 同样提供 Adreno GPU 支持，两者在移动端推理领域形成互补
- [[coremltools-9]] — Apple 端侧推理工具链，与 llama.cpp 的 iOS XCFramework 分发形成对比
- [[edgeflow-cold-start]] — 优化后的 OpenCL 后端可减少冷启动时的 GPU 初始化延迟
