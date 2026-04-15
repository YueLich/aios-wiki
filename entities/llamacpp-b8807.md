---
type: entity
tags: [inference, llama.cpp, vulkan, optimization, ggml]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8797]], [[gemma-cpp-inference]], [[edgeflow-cold-start]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8807
    title: "ggml-org/llama.cpp: b8807"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# llama.cpp b8807

> Vulkan 后端 im2col 优化——改善内存写入布局、限制工作组数、按厂商 ID 调优设备参数。2026-04-15 发布。

## 核心更新

b8807 主要聚焦 Vulkan 后端的 im2col 操作优化：

- **改善 im2col 内存写入布局**：优化卷积操作的中间结果存储方式，减少内存带宽瓶颈
- **限制工作组数量**：避免 GPU 资源过度分配导致的调度开销
- **按 vendor_id 而非 subgroup size 进行设备调优**：更通用的设备适配策略，subgroup size 在不同 GPU 上差异大，vendor_id 更稳定

## 支持平台

- macOS Apple Silicon (arm64) + KleidiAI 变体
- macOS Intel (x64)
- iOS XCFramework
- Linux: Ubuntu x64/arm64/s390x, Vulkan, ROCm 7.2, OpenVINO 2026.0
- Windows: x64/arm64 CPU, CUDA 12.4

## 为什么重要

im2col 是卷积神经网络推理的核心操作，视觉模型（图像分类、目标检测、OCR）大量使用。Vulkan 后端覆盖了大部分 Android 设备和 Linux 桌面 GPU。这次优化直接改善端侧视觉模型的推理性能——对手机端 Agent 的屏幕理解、图像识别等场景尤为重要。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的背景
- [[llamacpp-b8797]] — 上一个已记录版本
- [[gemma-cpp-inference]] — llama.cpp 推理生态
- [[edgeflow-cold-start]] — 端侧推理冷启动优化
