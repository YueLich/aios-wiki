---
type: entity
tags: [推理框架, llama.cpp, ggml, 推理引擎, 库重构, kleidiai]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8828]], [[llamacpp-b8827]], [[gemma-cpp-inference]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8829
    title: "llama.cpp b8829 release"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# llama.cpp b8829

> 库重命名重构 + KleidiAI arm64 支持增强

## 发布信息

- **版本**: b8829
- **发布日期**: 2026-04-17
- **仓库**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 核心变更

### libcommon → libllama-common 重命名

本次发布的主要变更是库重命名重构（#21936）：

- `libcommon` 重命名为 `libllama-common`
- 新增 `libllama-common-base` 子库
- CMake 配置允许共享库构建
- 添加 `-fPIC` 编译标志以支持位置无关代码
- 导出所有符号（export all symbols）
- 添加 `common_log_get_verbosity_thold()` API
- 修复 build_info 导出问题

### KleidiAI 支持

macOS arm64 构建新增 KleidiAI 启用版本，为 Arm 架构提供优化的推理加速。

### 平台支持

- macOS (Apple Silicon arm64 + KleidiAI / Intel x64)
- iOS XCFramework
- Linux (Ubuntu x64/arm64/s390x, Vulkan, ROCm 7.2, OpenVINO)
- Windows (x64/arm64, CPU/CUDA/Vulkan)

## 关键洞察

- 这是一个**重构型发布**，不包含新功能但改善了库结构
- `libllama-common` 的命名更清晰，表明 common 组件正在成为 llama.cpp 生态的正式基础设施
- KleidiAI arm64 构建对 **iPhone/iPad 端侧推理** 有直接价值
- ROCm 7.2 和 OpenVINO 2026.0 支持保持了多硬件后端覆盖

## 为什么重要

库重构虽然不直接影响终端用户，但对下游项目（MNN、MLC-LLM 等）的集成有长期影响。清晰的库边界使 llama.cpp 更适合作为基础推理层被其他框架依赖。

## 关联

- [[ggml-llamacpp-hf]] — GGML 与 HuggingFace 的合作，llama.cpp 生态的整体定位
- [[llamacpp-b8828]] — 前一个版本
- [[llamacpp-b8827]] — 近期版本系列
- [[gemma-cpp-inference]] — gemma.cpp 基于 GGML 的推理实现
