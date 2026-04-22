---
type: entity
tags: [推理框架, llama-cpp, ggml, 端侧推理, macOS, iOS]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[coremltools-9]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8840
    title: "llama.cpp b8840 Release"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# llama.cpp b8840

> llama.cpp 的 b8840 版本发布于 2026-04-18，主要更新为服务器端 API 增强。

## 核心更新

- **服务器 API**: 在 `/props` 端点暴露 `media_tag` 字段（PR #22028），增强了多媒体模型支持的元数据查询能力

## 平台支持

- **macOS**: Apple Silicon (arm64) + KleidiAI 加速变体、Intel x64
- **iOS**: XCFramework 包
- **Linux**: Ubuntu x64/arm64/s390x、Vulkan、ROCm 7.2、OpenVINO

## 为什么重要

b8840 虽然是小幅更新，但 `media_tag` 的暴露意味着 llama.cpp 正在加强对多模态模型（视觉+语言）的服务端支持。对于依赖 llama.cpp 做端侧推理的移动应用来说，多模态能力的完善是关键里程碑。

从 b8783 到 b8840（过去几周内 20+ 个版本），项目保持了极高的迭代速度，持续优化端侧推理性能。

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 的 GGML 格式背景与量化体系
- [[mnn-350]] — 阿里 MNN，另一个主流端侧推理框架
- [[coremltools-9]] — Apple Core ML 工具链，与 llama.cpp iOS 部署互补
