---
type: entity
tags: [llama.cpp, inference, metal, ios, on-device, framework]
related: [[llamacpp-b8793]], [[llamacpp-b8791]], [[ggml-llamacpp-hf]], [[gemma4-ondevice]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8795
    title: "llama.cpp b8795 Release"
    date: 2026-04-14
    reliability: high
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8794
    title: "llama.cpp b8794 Release"
    date: 2026-04-14
    reliability: high
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8793
    title: "llama.cpp b8793 Release"
    date: 2026-04-14
    reliability: high
created: 2026-04-15
updated: 2026-04-15
---

# llama.cpp b8793–b8795

> 连续三个版本在同一天发布（2026-04-14），涵盖 Vulkan 精度修复、多模态 API 扩展和 Metal FlashAttention 修复

## 核心变更

### b8795: Metal FlashAttention 修复
- **修复 FA 支持逻辑** (#21898)：修复 Apple Metal 后端的 FlashAttention 支持判断逻辑
- 对 iOS/macOS 端侧推理至关重要——FlashAttention 是移动端 Transformer 推理的关键加速手段
- 修复前可能导致某些设备上 FA 回退到慢速路径，严重影响推理延迟

### b8794: 多模态 API 扩展
- **新增 `mtmd_image_tokens_get_decoder_pos()` API** (#21851)：为多模态推理提供图像 token 解码位置查询
- 这是 llama.cpp 多模态能力（图像理解）的关键 API 补充
- 允许开发者精确控制图像 token 在序列中的位置，对手机端多模态应用（拍照问答、屏幕理解等）至关重要

### b8793: Vulkan 精度修复
- **Vulkan shader RoundingModeRTE** (#21572)：在设备支持时自动为所有 Vulkan shader 添加 RoundingModeRTE
- 使用 FetchContent 获取 SPIRV-Headers
- 修复 Vulkan 后端的数值精度问题，影响 Android 设备上的推理正确性

## 为什么重要

**对手机端 AI 生态的关键信号**：

1. **Metal FA 修复**直接提升 iPhone/iPad 端侧推理性能。FlashAttention 是 3B-7B 模型在移动设备上达到可用延迟（<500ms TTFT）的核心技术。

2. **多模态 API** 持续完善，说明 llama.cpp 正从纯文本推理引擎演变为多模态推理框架——这与 Apple Intelligence、Gemini Nano 等端侧多模态战略一致。

3. **Vulkan 精度修复**保障 Android 设备推理正确性。Vulkan 是 Android GPU 推理的主要后端，精度问题会导致模型输出错误。

4. **一天三版本**的发布频率反映了社区对移动端推理的极高关注度和活跃开发节奏。

## 平台支持

| 平台 | 变体 |
|------|------|
| macOS/iOS | arm64, arm64-KleidiAI, x64, iOS XCFramework |
| Linux | x64, arm64, s390x, Vulkan x64/arm64, ROCm 7.2, OpenVINO |
| Windows | x64, arm64, CUDA 12/13, Vulkan, SYCL, HIP |
| openEuler | 310p, 910b ACL Graph |

## 关联
- [[llamacpp-b8793]] — 前一版本，Vulkan 精度修复
- [[ggml-llamacpp-hf]] — llama.cpp 加入 HuggingFace 的背景
- [[gemma4-ondevice]] — 多模态模型，依赖此类推理框架
- [[coremltools-9]] — Apple 端侧推理工具链的另一条路径
- [[mnn-350]] — 阿里端侧推理框架，竞品对比
