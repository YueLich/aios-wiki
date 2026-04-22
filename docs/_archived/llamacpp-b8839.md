---
type: entity
tags: [推理框架, llama.cpp, ggml, 推理引擎, 端侧推理, 开源]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8838]], [[mnn-350]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8839
    title: "ggml-org/llama.cpp b8839 release"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# llama.cpp b8839

> 持续迭代的端侧 LLM 推理引擎，本版本聚焦模型层代码重构。

## 核心变更

- **模型层重构 (#22079)**: 重构 bias tensor 变量命名，统一 jina-bert-v2 等模型中 `create_tensor_qkv` 的使用方式。这是纯内部重构，不改变 API 或推理行为，但提升了代码可维护性。

## 平台支持

本版本继续提供完整的跨平台构建：

| 平台 | 构建 |
|------|------|
| macOS/iOS | arm64, x64, KleidiAI, XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan, ROCm 7.2, OpenVINO |
| Android | arm64 CPU |
| Windows | x64/arm64 CPU, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910B |

## 关键洞察

llama.cpp 保持极高的迭代频率（从 b8838 到 b8839 仅 1 个 commit），说明项目处于活跃维护状态。对于移动端 AIOS 开发者而言：

1. **iOS XCFramework**: 持续提供 iOS 原生集成支持，是 Core ML 之外的重要端侧推理选项
2. **Android arm64**: 直接可用的 Android 预编译二进制，降低端侧部署门槛
3. **KleidiAI 构建**: 针对 ARM 架构优化的推理路径，对移动端性能至关重要

## 为什么重要

llama.cpp 是端侧 LLM 推理的事实标准引擎。本版本虽为小幅重构，但体现了：
- 代码质量持续优化（变量命名规范化）
- 全平台覆盖无死角（iOS/Android/Linux/Windows 均有预编译包）
- 生态系统稳定（MNN、coremltools 等竞品/互补方案也在同步迭代）

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 主页与生态概述
- [[llamacpp-b8838]] — 前一版本，主要包含模型支持更新
- [[mnn-350]] — 阿里 MNN，另一端侧推理框架
- [[coremltools-9]] — Apple Core ML 工具链，llama.cpp XCFramework 的替代/互补方案
