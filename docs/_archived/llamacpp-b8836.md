---
type: entity
tags: [llama-cpp, inference-engine, ggml, release, 推理框架, 开源]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8831]], [[llamacpp-b8833]], [[mnn-350]], [[vllm-mlx-apple-silicon]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8836
    title: "ggml-org/llama.cpp: b8836"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# llama.cpp b8836

> llama.cpp b8836 发布于 2026-04-18，主要改进为 CI 基础设施优化（ROCm 发布磁盘空间释放），继续提供全平台预编译二进制。

## 版本概要

b8836 是一个维护性版本，变更内容集中在 CI/CD 流程：

- **核心变更**：释放 ROCm 发布流程中的磁盘空间（#22012）
- 无功能性代码变更

## 平台支持

延续全平台预编译策略：

| 平台 | 变体 |
|------|------|
| macOS Apple Silicon | CPU, KleidiAI 加速 |
| macOS Intel | CPU |
| iOS | XCFramework |
| Linux x64 | CPU, Vulkan, ROCm 7.2, OpenVINO |
| Linux arm64 | CPU, Vulkan |
| Linux s390x | CPU |
| Android arm64 | CPU |
| Windows x64 | CPU, CUDA 12 |
| Windows arm64 | CPU |

## 关键洞察

**持续高频迭代**：从 b8831 到 b8836 仅 5 个构建版本，体现了 llama.cpp 的极高迭代频率。这种日级发布节奏保证了端侧推理引擎能快速吸收社区贡献。

**ROCm 7.2 支持**：AMD ROCm 7.2 预编译版本的提供，意味着 AMD GPU 推理生态在 llama.cpp 中的成熟度提升，为 Linux 端侧推理提供了更多硬件选择。

## 为什么重要

llama.cpp 作为端侧 LLM 推理的核心引擎，每个版本都确保了最新模型的快速适配。对手机端 AIOS 而言，iOS XCFramework 和 Android arm64 的持续预编译保证了端侧部署的可用性。

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的生态整合
- [[llamacpp-b8831]], [[llamacpp-b8833]] — 近期版本对比
- [[mnn-350]] — 阿里 MNN 推理引擎，同为端侧推理竞争者
- [[vllm-mlx-apple-silicon]] — vLLM-MLX 在 Apple Silicon 的高性能推理
