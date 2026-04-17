---
type: entity
tags: [推理框架, llama.cpp, ggml, android, arm64, 端侧推理, 移动端部署]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8829]], [[llamacpp-b8828]], [[mnn-350]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8831
    title: "llama.cpp b8831 release"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# llama.cpp b8831

> 首个官方 Android arm64 构建发布 — llama.cpp 正式成为 Android 端侧推理一等公民

## 发布信息

- **版本**: b8831
- **发布日期**: 2026-04-17
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 核心变更

### Android arm64 官方构建（#21647）

本次发布的最大亮点是添加了 **Android arm64 CPU 官方构建和发布**：

- 新增 CI 流水线自动生成 Android arm64 二进制
- 使用 android-setup actions v4 固定版本
- 提供预编译的 Android arm64 CPU 包
- 与现有 macOS/iOS/Linux/Windows 构建并列发布

这意味着开发者不再需要自行交叉编译即可直接使用 llama.cpp 的 Android 版本。

### 其他变更

- **server**: 修复 `ignore_eos` 标志未被正确尊重的问题
- CI 流水线稳定性改进

### 完整平台支持矩阵

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | Apple Silicon arm64 | 含 KleidiAI 版本 |
| macOS | Intel x64 | — |
| iOS | XCFramework | — |
| Linux | Ubuntu x64/arm64/s390x | CPU/Vulkan/ROCm/OpenVINO |
| **Android** | **arm64** | **🆕 首次官方支持** |
| Windows | x64/arm64 | CPU/CUDA/Vulkan/SYCL/HIP |
| openEuler | x86/aarch64 | 310p/910b |

## 关键洞察

- **Android 一等公民化**：llama.cpp 从"可以在 Android 上编译"进化为"官方提供 Android 构建"。这是移动端端侧推理基础设施成熟的重要标志。
- **降低门槛**：此前 Android 开发者需要配置 NDK 交叉编译环境，现在可以直接下载预编译包集成到应用中。
- **生态信号**：HuggingFace 收购 GGML/llama.cpp 后，平台支持在快速扩展。Android 官方支持表明社区对移动 AI 推理的重视在持续增长。
- **与 MNN 竞争**：alibaba/MNN 3.5.0 已有完善的 Android 支持，llama.cpp 的加入为开发者提供了更多选择。

## 为什么重要

Android 是全球最大的移动平台。llama.cpp 提供官方 Android 构建意味着：
1. 端侧 LLM 部署在 Android 上的工具链更加完整
2. 开发者可以在 Android 应用中更便捷地集成本地推理能力
3. 与 Apple Core ML 生态形成对称的双平台支持格局
4. 为 Gemma、Llama 等模型在 Android 上的本地运行扫清了构建障碍

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 后的平台扩展
- [[llamacpp-b8829]] — 上一版本：库重构 + KleidiAI 支持
- [[mnn-350]] — MNN 3.5.0：Android 端侧推理的另一选择
- [[gemma-cpp-inference]] — gemma.cpp：同生态的 Google 模型推理
- [[android-cli-agent-workflow]] — Android CLI 工具链生态
