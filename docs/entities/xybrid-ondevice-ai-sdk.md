---
type: entity
tags: [rust, on-device, llm, asr, tts, sdk, ios, android, flutter, unity, offline]
related: [[mnn-350]], [[ggml-llamacpp-hf]], [[litertlm-swift]], [[gemma4-ondevice]]
sources:
  - url: https://github.com/xybrid-ai/xybrid
    title: "Xybrid: Run LLMs, ASR, and TTS natively in apps and games"
    date: 2026-04-15
    reliability: medium
  - url: https://news.ycombinator.com/item?id=47427332
    title: "Show HN: Xybrid – run LLM and speech locally in your app (no back end, Rust)"
    date: 2026-04-12
    reliability: low
created: 2026-04-19
updated: 2026-04-19
---

# Xybrid

> Rust核心的端侧AI SDK，支持LLM/ASR/TTS本地推理，覆盖iOS/Android/Flutter/Unity。私有、离线、无需云端。GitHub 140⭐。

## 核心问题

移动应用和游戏需要在设备本地运行AI（语音助手、NPC对话、实时翻译等），但现有方案要么需要云端API（延迟+隐私问题），要么集成复杂（多个引擎、平台差异）。

## 方法/架构

**架构**：Rust核心 + 多平台SDK
- **Rust核心**：高性能推理引擎
- **平台SDK**：iOS (Swift)、Android (Kotlin)、Flutter (Dart)、Unity (C#)
- **三合一**：LLM推理 + ASR（语音识别）+ TTS（语音合成）统一在一个SDK中
- **完全离线**：无需后端服务器或守护进程

**支持模型**：通过[xybrid.ai/models](https://www.xybrid.ai/models)提供预优化模型。

## 为什么重要

- 统一了端侧LLM/ASR/TTS的集成体验，降低开发者门槛
- Rust核心保证跨平台性能一致性
- 对比[[mnn-350]]（阿里）和[[ggml-llamacpp-hf]]（社区），Xybrid专注于应用层SDK体验而非底层推理引擎
- Flutter/Unity支持覆盖了游戏和跨平台应用这一被忽视的市场

## 关联
- [[mnn-350]] — 阿里端侧推理引擎
- [[ggml-llamacpp-hf]] — llama.cpp推理框架
- [[litertlm-swift]] — iOS端侧LLM Swift封装
- [[gemma4-ondevice]] — Google端侧模型
