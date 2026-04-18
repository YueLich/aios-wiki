---
type: entity
tags: [模型, Gemma, Google, 端侧推理, AICore, 多模态, agentic]
related: [[gemini-31-flash-lite]], [[gemma-3-2b]], [[minicpm-242]], [[on-device-inference-memory-pressure]], [[android-agent-assistant]]
sources:
  - url: https://deepmind.google/blog/gemma-4-byte-for-byte-the-most-capable-open-models/
    title: "Gemma 4: Byte for byte, the most capable open models"
    date: 2026-04-02
    reliability: high
  - url: https://android-developers.googleblog.com/2026/04/AI-Core-Developer-Preview.html
    title: "Announcing Gemma 4 in the AICore Developer Preview"
    date: 2026-04-02
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# Gemma 4: 端侧开源模型新标杆

> Google DeepMind 发布的最新开源模型家族，专为端侧推理和 Agent 工作流设计，是 Gemini Nano 4 的基础。

## 核心问题
端侧设备（手机、平板、穿戴设备）需要强大的 AI 能力，但受限于算力、内存和功耗。现有开源模型在端侧部署时，要么能力不足（简单对话），要么体积过大（无法在移动设备上运行）。Gemma 4 旨在提供"每字节最高智能密度"的开源模型。

## 模型架构与规格

Gemma 4 提供四个尺寸变体，覆盖从旗舰手机到高端服务器的全场景：

| 变体 | 参数量 | 架构 | 目标硬件 | 关键特性 |
|------|--------|------|---------|---------|
| E2B (Effective 2B) | ~2B | Dense | 旗舰手机/穿戴 | 多模态、低延迟、电池优化 |
| E4B (Effective 4B) | ~4B | Dense | 手机/平板 | 平衡性能与效率 |
| 26B MoE | 26B 总参/~4B 活跃 | Mixture of Experts | 桌面/边缘服务器 | 高性能稀疏激活 |
| 31B Dense | 31B | Dense | GPU 服务器 | 最大推理能力 |

**E2B 和 E4B** 是端侧部署的核心：原生支持 140+ 语言、多模态输入（图像+文本）、低延迟处理。相比前代模型，速度快 4 倍，功耗降低 60%。

## AICore 集成

Gemma 4 是下一代 Gemini Nano 的基础。通过 AICore Developer Preview，开发者可以：
- 直接在 AICore 启用设备上测试
- 使用 Google、MediaTek、Qualcomm 最新 AI 加速器
- 提前适配 Gemini Nano 4 API（代码自动兼容）

```kotlin
val previewFullConfig = generationConfig {
    modelConfig = ModelConfig {
        releaseTrack = ModelReleaseTrack.PREVIEW
        // ...
    }
}
```

**即将支持**：Tool Calling、结构化输出、System Prompt、Thinking Mode（Prompt API）。

## 关键洞察

1. **MoE 架构是端侧的未来**：26B MoE 变体只激活 ~4B 参数，却能达到接近 31B Dense 的性能。这种稀疏激活模式天然适合功耗受限的移动设备——只在需要时消耗算力。

2. **"Effective" 参数量命名**：Google 不再强调原始参数量，而是强调"有效计算等效参数"。E2B 的命名暗示它在实际任务中的表现相当于传统 2B dense 模型，但多模态能力更强。这反映了端侧 AI 从"参数竞赛"转向"智能密度"的趋势。

3. **AICore 作为 Android AI 抽象层**：Gemma 4 通过 AICore 访问，而非直接调用底层推理引擎。这意味着模型可以利用 OEM 厂商（高通、联发科）的硬件优化，同时保持 API 一致性。开发者无需关心具体是 NPU 还是 GPU 运行推理。

4. **从 Gemma 3 到 Gemma 4 的飞跃**：前代 Gemma 3 2B 在端侧主要支持基础文本生成。Gemma 4 E2B 原生支持多模态、140+ 语言、Agent 工作流，是端侧模型能力的一次重大跨越。

## 为什么重要

Gemma 4 代表了端侧开源模型的拐点：
- **开发者不再需要在能力与效率之间二选一**——E2B 提供多模态+Agent 能力，同时保持手机可用的推理速度
- **AICore 集成消除了碎片化**——一套 API 适配所有 Android OEM 的 AI 加速器
- **开源意味着可微调**——开发者可以在端侧 fine-tune Gemma 4 以实现特定任务的 SOTA 性能
- **为 Android Agent 生态奠定基础**——Gemma 4 + AICore + Android Skills = 完整的端侧 Agent 开发栈

## 关联
- [[gemini-31-flash-lite]] — 同期发布的轻量级 Gemini 变体，云端推理优化
- [[gemma-3-2b]] — Gemma 系列前代端侧模型
- [[minicpm-242]] — 开源端侧模型的另一个选择
- [[on-device-inference-memory-pressure]] — 端侧推理的内存管理挑战
- [[android-agent-assistant]] — 基于 Android 的 Agent 系统
- [[ggml-llamacpp-hf]] — Gemma 4 可通过 llama.cpp 在非 Android 设备上运行
