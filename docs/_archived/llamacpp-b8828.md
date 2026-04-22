---
type: entity
tags: [llama.cpp, ggml, gemma4, inference, on-device, model-detection, 推理框架]
related: [[llamacpp-b8827]], [[gemma4-ondevice]], [[ggml-llamacpp-hf]], [[gemma-cpp-inference]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8828
    title: "ggml-org/llama.cpp: b8828"
    date: 2026-04-17
    reliability: high
  - url: https://github.com/ggml-org/llama.cpp/pull/22027
    title: "PR #22027: model : Gemma4 model type detection"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# llama.cpp b8828

> 新增 Gemma4 模型类型自动检测，修复 llama-bench 等工具中 Gemma4 31B/26BA4B 显示为 "?B" 的问题。

## 核心更新

本次发布的焦点是 PR #22027：**Gemma4 模型类型检测**。这是一个看似微小但对端侧生态意义重大的修复。

### 技术细节

- **模型类型自动识别**：新增 Gemma4 31B 和 26BA4B（26B 激活参数，4B 模型分片）两种变体的类型检测逻辑
- **纯展示性修复**：不改变推理行为，修正 `llama-bench`、`llama-server` 等工具中 Gemma4 模型的参数量显示
- **代码改动极小**：仅修改 2 个文件，+7/-1 行 — 说明是精准的元数据修补而非大规模重构
- **覆盖两种 Gemma4 变体**：
  - **Gemma4 31B**：完整参数量 31B 的模型
  - **Gemma4 26BA4B**：MoE 风格架构，26B 激活参数，4B 分片大小

### 平台支持

b8828 继续提供全面的跨平台二进制分发，与 b8827 一致：

| 平台 | 变体 |
|------|------|
| macOS | arm64, arm64 KleidiAI, x64 |
| iOS | XCFramework |
| Linux | x64/arm64/s390x CPU, Vulkan, ROCm 7.2, OpenVINO |
| Windows | x64/arm64 CPU, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910b ACL Graph |

## 为什么重要

对手机端 AIOS 生态而言：

- **Gemma4 是 Google 端侧 LLM 主力**：Google 正将 Gemma4 作为 on-device AI 核心模型推广，llama.cpp 作为最流行的本地推理框架，Gemma4 支持的完善程度直接影响开发者体验
- **模型类型检测是工具链基础**：错误的参数量显示会导致 benchmark 失真、资源预估错误、量化配置不匹配 — 这些在端侧资源受限的设备上尤为关键
- **26BA4B 的特殊架构需要显式支持**：MoE 风格的 Gemma4 变体在端侧推理时的内存占用和延迟特性与 dense 31B 完全不同，自动检测确保工具链能正确区分
- **从 b8827 的 OpenCL Adreno 到 b8828 的 Gemma4 支持**：llama.cpp 在移动端推理上的迭代速度持续保持高位

## 关联

- [[llamacpp-b8827]] — 前一个版本，OpenCL Adreno GPU 调度重构
- [[gemma4-ondevice]] — Gemma4 端侧部署的详细概述
- [[ggml-llamacpp-hf]] — GGML 与 llama.cpp 加入 HuggingFace 的生态概述
- [[gemma-cpp-inference]] — Google 官方的 Gemma C++ 推理实现
