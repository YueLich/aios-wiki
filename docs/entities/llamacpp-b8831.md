---
type: entity
tags: [llama.cpp, inference, android, mobile, 推理框架, 端侧部署]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[minicpm-242]], [[gemma4-ondevice]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8831
    title: "llama.cpp b8831"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# llama.cpp b8831 — Android arm64 官方构建

> 里程碑版本：首次提供官方 Android arm64 预编译包，极大降低手机端 LLM 推理部署门槛。

## 核心更新

### Android arm64 官方构建（#21647）
b8831 最重要的变化是 **CI 新增 Android arm64 构建和发布流程**。此前，Android 用户需要自行交叉编译或依赖社区构建。现在可以直接下载预编译的 `llama-b8831-bin-android-arm64.tar.gz`。

这对手机端 AIOS 意义重大：
- **降低部署门槛**：开发者不再需要配置 NDK 交叉编译环境
- **标准化二进制**：官方构建经过 CI 测试，质量有保障
- **持续更新**：每次 release 自动构建，用户始终能获取最新版本

### 全平台支持矩阵

| 平台 | 架构 | 加速后端 |
|------|------|---------|
| macOS | arm64, x64 | Metal, KleidiAI |
| iOS | XCFramework | Metal |
| Linux | x64, arm64, s390x | CPU, Vulkan, ROCm 7.2, OpenVINO |
| **Android** | **arm64** | **CPU** |
| Windows | x64, arm64 | CPU, CUDA 12.4, CUDA 13.1, Vulkan, SYCL, HIP |

### 其他改进
- server: 修复 ignore_eos 标志未被尊重的问题
- pin android-setup actions 到 v4（CI 稳定性）

## 为什么重要

1. **Android 官方支持是信号**：ggml-org 正式将 Android 作为一等公民平台，意味着手机端 LLM 推理从"社区hack"变为"官方支持"
2. **端到端部署路径成熟**：从模型量化（GGUF）→ 二进制下载 → Android App 集成，全链路可用
3. **生态协同**：配合 MNN、CoreML、TensorRT 等其他推理框架，llama.cpp 在 CPU 推理场景（尤其是 ARM 设备）保持领先

## 关联

- [[ggml-llamacpp-hf]] — llama.cpp 与 HuggingFace 生态整合
- [[mnn-350]] — 阿里 MNN 推理框架，同为端侧推理选择
- [[minicpm-242]] — MiniCPM 模型可在 llama.cpp 上运行
- [[gemma4-ondevice]] — Gemma 4 等模型的端侧部署
