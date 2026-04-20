---
type: entity
tags: [asr, mlx, coreml, apple-silicon, whisper, streaming, speech, 实时转录, 推理优化]
related: [[whisper]], [[coremltools-9]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://github.com/altalt-org/Lightning-SimulWhisper
    title: "Lightning-SimulWhisper GitHub"
    date: 2026-04-20
    reliability: high
  - url: https://news.ycombinator.com/item?id=47774971
    title: "HN: Lightning-SimulWhisper"
    date: 2026-04-20
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# Lightning-SimulWhisper

> 基于 MLX + CoreML 的实时流式语音转录引擎，在 Apple Silicon 上实现 15-18x 加速，支持 large-v3-turbo 模型实时运行。

## 核心问题

OpenAI 的 Whisper 模型在通用 GPU 上推理速度有限。在 Apple Silicon 设备上，原始 PyTorch 实现只能勉强运行 `base` 模型实时转录，`medium` 和 `large` 模型完全无法实时。这严重限制了端侧语音助手和实时字幕应用的实用性。

## 方法/架构

Lightning-SimulWhisper 采用双引擎架构，结合 MLX 和 CoreML 的优势：

- **CoreML Encoder**：利用 Apple Neural Engine (ANE) 加速编码器，最高 18x 加速。通过 `coremltools` 将 Whisper 编码器转换为 CoreML 格式，直接在 ANE 上执行。
- **MLX Decoder**：Apple 的 MLX 框架优化解码器推理，最高 15x 加速。MLX 提供原生 Apple Silicon 优化，避免了 PyTorch 的开销。
- **AlignAtt Policy**：采用 SimulStreaming 论文的 AlignAtt 对齐策略实现流式解码，同时保持转录质量。
- **零 PyTorch 依赖**：完全移除 PyTorch，仅依赖 MLX 和 CoreML，显著降低内存占用和启动时间。

支持模型：`tiny.en`, `tiny`, `base.en`, `base`, `small.en`, `small`, `medium.en`, `medium`, `large-v1`, `large-v2`, `large-v3`, `large-v3-turbo`

## 关键数据

| 指标 | PyTorch 基线 | MLX+CoreML | 加速比 |
|------|------------|-----------|--------|
| 编码器速度 | 1x | 18x | 18x |
| 解码器速度 | 1x | 15x | 15x |
| 可实时模型 | base | medium, large-v3-turbo | — |
| 功耗 | 高 | CoreML 显著更低 | — |

GitHub Stars: 560+

## 关键洞察

1. **CoreML Encoder 是关键**：MLX-only 版本功耗过高（"consumes way too much power"），CoreML 编码器利用 ANE 硬件加速大幅降低功耗。这验证了在 Apple Silicon 上，混合使用 CoreML（编码器）和 MLX（解码器）是最优策略。

2. **端侧 ASR 的天花板在提升**：从只能运行 base 模型到能实时运行 large-v3-turbo，这意味着端侧语音助手的准确度可以接近云端方案。

3. **功耗测试缺失是机会**：项目作者坦言不知道如何测量特定进程的功耗。这是一个有价值的贡献方向——Apple Silicon 的功耗特性数据对端侧 AI 优化至关重要。

## 为什么重要

对手机端 AI 生态的意义：
- **Apple 生态的端侧 ASR 范式**：展示了如何在 Apple 设备上高效运行 Whisper，为 iOS/macOS 语音应用提供了参考实现
- **CoreML + MLX 混合推理**：这一架构模式可推广到其他模型（视觉、语言），是 Apple AI 生态的核心推理模式
- **实时流式推理**：AlignAtt 策略实现低延迟流式转录，对端侧 AI 助手的语音交互至关重要

## 关联

- [[whisper]] — Lightning-SimulWhisper 的基础模型，OpenAI 的通用 ASR 模型
- [[coremltools-9]] — 用于将 Whisper 编码器转换为 CoreML 格式的工具链
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[gemma4-ondevice]] — 同为端侧推理方案，但针对语言模型而非 ASR
