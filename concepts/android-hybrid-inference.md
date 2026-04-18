---
type: concept
tags: [android, hybrid-inference, gemini, firebase, on-device, edge-cloud, 端云协同, 推理优化]
related: [[gemini-nano-chrome137]], [[gemma4-ondevice]], [[edgeflow-cold-start]], [[on-device-vs-cloud-agentic-tool-calling]], [[comllm-mec-offloading]]
sources:
  - url: https://android-developers.googleblog.com/2026/04/Hybrid-inference-and-new-AI-models-are-coming-to-Android.html
    title: "Experimental hybrid inference and new Gemini models for Android"
    date: 2026-04-17
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# Android Hybrid Inference: Firebase AI Logic 端云协同 API

> Google 发布 Firebase AI Logic 混合推理 API，让 Android 应用可在 Gemini Nano（端侧）与云端 Gemini 模型之间动态切换，标志着 Android 端云协同 AI 推理走向标准化。

## 核心问题

Android 开发者在实现 AI 功能时面临一个根本性选择：使用端侧模型（低延迟、离线可用、隐私好，但能力有限）还是云端模型（能力强、始终最新，但依赖网络、有延迟和成本）。

传统做法需要开发者自行实现路由逻辑，在两个完全不同的 API 之间切换。这增加了开发复杂度，且大多数应用选择了单一方案而非真正利用两者优势。

## 方法/架构

Firebase AI Logic 推出了 **Hybrid Inference API**，核心设计：

**统一 API 接口**：通过单一 `GenerativeModel` 接口，开发者配置推理模式即可：
- `PREFER_ON_DEVICE`：优先使用 Gemini Nano，不可用时回退到云端
- `PREFER_IN_CLOUD`：优先云端，离线时回退到端侧

**技术栈**：
- 端侧执行：通过 ML Kit Prompt API 调用 Gemini Nano
- 云端推理：支持 Vertex AI 和 Developer API 的所有 Gemini 模型
- 新增支持：Gemini 3.1 Flash Lite 模型 + Nano Banana 图像生成模型

**依赖配置**：
```kotlin
implementation("com.google.firebase:firebase-ai:17.11.0")
implementation("com.google.firebase:firebase-ai-ondevice:16.0.0-beta01")
```

**当前限制**（仍为实验性）：
- 端侧模型仅支持单轮文本生成
- 输入限制为文本或单张 Bitmap 图片
- 路由策略为简单规则型，未来计划提供更智能的路由

## 关键洞察

**1. 端云协同从应用层下沉到框架层**
这标志着端云协同模式从"开发者自行实现"演进为"平台原生提供"。Firebase 把路由逻辑封装为框架能力，降低了端云协同的门槛。对移动 AIOS 生态而言，这意味着端侧推理不再是可选优化，而是默认路径的一部分。

**2. 规则路由 vs 智能路由**
当前实现是简单的 `PREFER_ON_DEVICE` / `PREFER_IN_CLOUD` 规则切换，但 Google 明确表示未来会提供"更复杂的路由能力"。这暗示后续可能引入基于任务复杂度、网络状况、隐私需求的智能路由——这正是 [[comllm-mec-offloading]] 和 [[on-device-vs-cloud-agentic-tool-calling]] 中讨论的核心问题。

**3. Gemini Nano 的战略定位**
通过 Firebase AI Logic 把 Gemini Nano 包装为端侧推理后端，Google 实现了与云端 Gemini 的无缝集成。开发者不需要了解模型细节，只需选择推理模式。这种抽象层的设计理念与 [[gemma4-ondevice]] 的端侧推理优化思路一脉相承。

## 为什么重要

1. **标准化端云协同接口**：这是 Android 生态中首个官方的端云混合推理 API，将影响整个移动端 AI 开发范式
2. **降低端侧 AI 门槛**：开发者不再需要同时维护端侧和云端两套代码，一个 API 解决两种场景
3. **Agent 架构的基础设施**：未来的 Android AI Agent 需要根据任务复杂度动态选择推理路径，Hybrid Inference API 提供了这一基础能力
4. **竞争格局**：与 Apple 的 [[anylanguagemodel-apple]] 统一 API 理念类似，Google 在 Android 端也在推动端侧与云端推理的统一抽象

## 关联
- [[gemini-nano-chrome137]] — Gemini Nano 从 Chrome 扩展到 Android，端侧推理覆盖更多平台
- [[gemma4-ondevice]] — Gemma 4 端侧推理优化，Hybrid Inference API 可能未来支持更多端侧模型
- [[edgeflow-cold-start]] — 端侧模型冷启动优化，影响 `PREFER_ON_DEVICE` 的实际用户体验
- [[on-device-vs-cloud-agentic-tool-calling]] — Agent 工具调用的端云选择策略，Hybrid API 提供了底层支持
- [[comllm-mec-offloading]] — 边缘计算卸载的理论框架，Hybrid Inference 是其工程实现之一
- [[react-native-llm-edge]] — React Native 端侧 LLM 集成，Hybrid API 可能为跨平台开发提供参考
