---
type: entity
tags: [推理框架, iOS, LiteRT, Gemma, on-device, multimodal, Swift]
related: [[gemma4-ondevice]], [[google-ai-edge-gallery]], [[gemma-cpp-inference]], [[coremltools-9]]
sources:
  - url: https://github.com/mylovelycodes/LiteRTLM-Swift
    title: "LiteRTLM-Swift: Swift package for running LiteRT-LM models on iOS"
    date: 2026-04-16
    reliability: high
  - url: https://github.com/google-ai-edge/LiteRT-LM
    title: "Google LiteRT-LM (upstream C API)"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# LiteRTLM-Swift

> 社区项目，将 Google LiteRT-LM C API 封装为 Swift async/await 接口，在 iOS 上运行 Gemma 4 E2B 多模态推理。支持文本生成、视觉理解、音频理解和流式输出。

## 核心问题

Google 的 LiteRT-LM 提供了强大的端侧推理 C API，但 iOS 开发者缺乏原生 Swift 封装。直接使用 C API 需要手动管理内存、线程安全和模型生命周期，门槛极高。LiteRTLM-Swift 填补了这一空白，让 iOS 开发者可以像使用任何其他 Swift 库一样使用端侧大模型。

## 架构与能力

### 支持的推理模式

| 模式 | 方法 | 说明 |
|------|------|------|
| 文本生成 | `generate()` / `generateStreaming()` | 需要 Gemma 4 turn marker 格式 |
| 单图理解 | `vision(imageData:prompt:)` | 支持 JPEG/PNG/HEIC |
| 多图理解 | `visionMultiImage(imagesData:prompt:)` | 跨图比较 |
| 音频理解 | `audio(audioData:prompt:format:)` | WAV/FLAC/MP3，自动 16kHz 重采样 |
| 多模态融合 | `multimodal(audioData:imagesData:prompt:)` | 音频 + 图像联合推理 |
| 多轮对话（文本） | `openSession()` / `sessionGenerateStreaming()` | KV Cache 复用 |
| 多轮对话（多模态） | `openConversation()` / `conversationSend()` | 任意组合音频/图像/文本 |

### KV Cache 复用：关键性能优化

多轮对话的核心优化在于 KV Cache 复用：
- **首轮 TTFT**：~15-20 秒（完整 prefill）
- **后续轮次 TTFT**：~1-2 秒（增量 prefill，仅处理新 token）

这意味着在 iPhone 上运行多轮对话的体验接近云端 API 的延迟水平，但完全离线。

### 硬件要求

- iOS 17.0+，Xcode 16+
- iPhone 13 Pro 或更高（6 GB+ RAM）
- 需要 `increased-memory-limit` entitlement（模型加载需要 ~4 GB RAM）
- 模型大小：~2.6 GB（Gemma 4 E2B，从 HuggingFace 下载）

### 架构设计

```
┌──────────────────────────────────────────┐
│            Your iOS App                  │
├──────────────────────────────────────────┤
│           LiteRTLMSwift                  │
│  ┌──────────────────┐ ┌────────────────┐ │
│  │ LiteRTLMEngine   │ │ ModelDownloader│ │
│  │ .generate()      │ │ .download()    │ │
│  │ .vision()        │ │ .pause()       │ │
│  │ .audio()         │ │ .cancel()      │ │
│  │ .multimodal()    │ │                │ │
│  │ .openSession()   │ │                │ │
│  └────────┬─────────┘ └────────────────┘ │
│      Serial DispatchQueue (线程安全)      │
├──────────────────────────────────────────┤
│      CLiteRTLM.xcframework (C API)       │
│   Session API (文本)  │  Conversation API │
│                      │  (多模态 JSON)     │
└──────────────────────────────────────────┘
```

两个 API 层：
- **Session API**：原始文本 prompt，开发者控制格式。用于 `generate()` 系列方法。
- **Conversation API**：基于 JSON 的消息格式，内部处理图像解码/缩放/patchify 和音频解码/重采样/Mel 频谱图。

所有 C API 调用通过串行 DispatchQueue 序列化确保线程安全（LiteRT-LM 同时只支持一个活跃 session）。

## 构建 XCFramework

预构建的 `CLiteRTLM.xcframework` 已包含在仓库中。如需从源码构建：
- 需要 Bazel 7.6.1 + Xcode 16 + ~20 GB 磁盘空间
- 运行 `./scripts/build-xcframework.sh` 自动克隆并构建
- 支持 `ios_arm64`（真机）和 `ios_sim_arm64`（模拟器）

## 为什么重要

1. **端侧多模态推理的开发者体验革命**：这是首个提供完整 Swift async/await 封装的端侧大模型推理库，让 iOS 开发者可以零 C 代码使用 Gemma 4 的文本+视觉+音频能力。
2. **KV Cache 复用实现可用延迟**：15-20s → 1-2s 的 TTFT 跨越了从"技术演示"到"可用产品"的门槛。
3. **社区驱动的端侧生态**：非 Google 官方项目，说明社区正在主动填补端侧 AI 的工具链空白。
4. **与 [[coremltools-9]] 和 [[google-ai-edge-gallery]] 互补**：Core ML 提供通用 ML 推理，LiteRT-LM 专注于 LLM/VLM 推理，两者覆盖不同场景。

## 关联

- [[gemma4-ondevice]] — Gemma 4 是 LiteRTLM-Swift 默认支持的模型
- [[google-ai-edge-gallery]] — Google 官方端侧 AI 演示应用，使用相同底层 API
- [[gemma-cpp-inference]] — C++ 端侧推理方案，LiteRTLM-Swift 是其 Swift 封装
- [[coremltools-9]] — Apple 官方 ML 框架，与 LiteRT 覆盖不同推理场景
