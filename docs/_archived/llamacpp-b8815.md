---
type: entity
tags: [inference, llama-cpp, ggml, metal, apple-silicon, release]
related: [[ggml-llamacpp-hf]], [[llamacpp-b8809]], [[llamacpp-b8808]], [[llamacpp-b8807]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8815
    title: "ggml-org/llama.cpp: b8815"
    date: 2026-04-16
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# llama.cpp b8815

> 新增 Metal ROLL 算子实现 + 统一 Apple SDK 支持

## 更新内容

### Metal: 实现 ROLL 算子 (#21946)
- 在 Metal 后端新增 `ROLL` 操作的 GPU 实现
- 对 Apple Silicon 设备的推理性能有直接提升
- ROLL 操作在张量操作中用于序列位置变换，对注意力机制实现有辅助作用

### Unix: 支持统一 Apple SDK
- 支持 Apple 统一 SDK 架构
- 简化 macOS/iOS/tvOS 跨平台构建流程
- 为 [[coremltools-9]] 集成提供更好的 SDK 兼容性

## 为什么重要

对手机端 AI 生态的意义：

- **Metal 算子库持续完善**：ROLL 算子的 Metal 实现意味着更多底层操作可以在 Apple GPU 上执行，减少 CPU-GPU 数据搬运
- **统一 SDK 降低跨端部署门槛**：构建一次，部署到 iPhone/iPad/Mac，简化端侧模型部署流程
- **与 [[ggml-llamacpp-hf]] 的 HuggingFace 整合形成完整工具链**：从模型获取到端侧推理的全链路优化

## 关联
- [[ggml-llamacpp-hf]] — GGML 与 llama.cpp 加入 HuggingFace
- [[llamacpp-b8809]] — 上一版本
- [[llamacpp-b8808]] — 历史版本
- [[coremltools-9]] — Apple Core ML 工具链
