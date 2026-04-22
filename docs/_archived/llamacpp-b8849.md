---
type: entity
tags: [llama.cpp, inference, ggml, open-source, cross-platform, android]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[minicpm-242]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8849
    title: "llama.cpp b8849 Release"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# llama.cpp b8849

> GGML 推理引擎最新版本，支持 Android、iOS、macOS、Linux、Windows 多平台。小版本更新，改进 tool call 解析。

## 版本信息

- **发布日期**：2026-04-19
- **构建号**：b8849
- **仓库**：[ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 本次更新

```
common/autoparser: allow space after tool call (#22073)
```

这是一个小幅改进版本，主要修复了 tool call 解析中空格处理的问题。在 Agent 系统中，LLM 输出的 tool call 格式可能存在尾随空格，此修复提升了工具调用的鲁棒性。

## 多平台支持

llama.cpp 持续为端侧推理提供最广泛的平台覆盖：

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | arm64, x64 | Apple Silicon + Intel |
| iOS | XCFramework | 移动端完整支持 |
| Android | arm64 | 手机端推理核心 |
| Linux | x64, arm64, s390x | 服务器/边缘 |
| Windows | x64, arm64 | CUDA 12/13, Vulkan, SYCL |
| openEuler | x86 | 310p, 910b ACL Graph |

### 硬件加速选项
- **CUDA**: 12.4, 13.1
- **Vulkan**: 跨平台 GPU 推理
- **ROCm 7.2**: AMD GPU
- **OpenVINO**: Intel 推理优化
- **KleidiAI**: macOS ARM 优化
- **SYCL**: Intel oneAPI
- **HIP**: AMD Radeon

## 对手机端 AI 的意义

1. **Android arm64 构建**：直接可用于 Android 端侧 LLM 部署
2. **iOS XCFramework**：Swift/SwiftUI 项目可直接集成
3. **Tool Call 改进**：Agent 系统中工具调用的可靠性提升，对端侧 Agent 至关重要
4. **KleidiAI 支持**：Apple Silicon 上的推理加速，对 macOS/iOS 端侧部署有直接影响

## 关联
- [[ggml-llamacpp-hf]] — llama.cpp 的完整介绍和使用指南
- [[mnn-350]] — 阿里 MNN，另一个端侧推理引擎
- [[minicpm-242]] — MiniCPM 模型可使用 llama.cpp 推理
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[edgeflow-cold-start]] — 端侧推理引擎的冷启动优化
