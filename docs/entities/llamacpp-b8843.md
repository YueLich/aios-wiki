---
type: entity
tags: [推理框架, llama.cpp, GGML, CMake, MSVC, 热修复]
related: [[ggml-llamacpp-hf]], [[mnn-350]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8843
    title: "ggml-org/llama.cpp: b8843"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# llama.cpp b8843：MSVC 构建热修复

> 修复 b8838 引入的 CMake CMP0194 策略导致 Windows MSVC 构建失败的问题。该策略使 CMake 在 Windows 上优先选择 MinGW 工具链处理 ASM，破坏了 MSVC 构建。

## 修复内容

- **#21630 的副作用**：添加 CMP0194 NEW 策略消除 CMake 4.1+ 警告，但在 Windows runner 上导致 MinGW 工具链被优先选择
- **修复方式**：仅回滚 CMP0194 策略块，保留 #21630 的其他改进
- **权衡**：CMake 4.1+ 警告回归，但仅是外观问题，不破坏任何平台

## 可用构建

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | Apple Silicon (arm64) | 含 KleidiAI 版本 |
| macOS | Intel (x64) | — |
| iOS | XCFramework | — |
| Linux | x64/arm64/s390x | CPU/Vulkan/ROCm/OpenVINO |
| Android | arm64 | CPU |
| Windows | x64/arm64 | CPU/CUDA 12/CUDA 13/Vulkan/SYCL |

## 为什么重要

llama.cpp 是端侧 LLM 推理的基础设施级项目，Windows 构建失败直接影响大量开发者。b8843 作为热修复确保了跨平台可用性。连续的构建发布（b8841→b8842→b8843 在同一天内）也反映了项目对 Windows 生态的重视。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 的 GGUF 生态全貌
- [[mnn-350]] — 阿里 MNN 是另一个端侧推理引擎选项
- [[coremltools-9]] — Apple Core ML 工具链与 iOS XCFramework 构建互补
