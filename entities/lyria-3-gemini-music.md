---
type: entity
tags: [音乐生成, Gemini, 多模态, Lyria, DeepMind, 创作工具]
related: [[nano-banana-2-imagegen]], [[gemma4-ondevice]], [[gemini-on-device-android]]
sources:
  - url: https://deepmind.google/blog/a-new-way-to-express-yourself-gemini-can-now-create-music/
    title: "A new way to express yourself: Gemini can now create music"
    date: 2026-02-18
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Lyria 3 / Gemini 音乐生成

> Google DeepMind 的第三代音乐生成模型 Lyria 3 集成到 Gemini App，支持通过文本描述或图像生成 30 秒音乐片段。

## 核心功能

- **文本生成音乐**：描述音乐风格、情绪、乐器组合，生成 30 秒完整音轨
- **图像生成音乐**：上传图片，AI 根据视觉内容（场景、氛围、色彩）生成匹配的音乐
- **自动生成封面**：每次生成音乐的同时生成配套封面艺术
- **SynthID 水印**：所有生成音轨嵌入不可感知的 AI 水印用于溯源

## 技术架构

Lyria 3 基于 DeepMind 的音乐生成研究，采用：
- 多模态输入理解（文本 + 图像 → 音频 token）
- 音频 token 化：将音乐编码为离散 token 序列，类似 LLM 的文本 token
- 自回归生成 + 扩散模型混合架构
- 音质优化：支持多乐器、多轨混合、节奏同步

## 端侧部署潜力

30 秒音频的 token 数量相对可控（远少于长视频生成），理论上适合端侧部署：
- 音频 token 生成可在 NPU 上高效运行
- 模型体积可通过量化压缩到移动端可接受范围
- 实时音乐生成 + 编辑的端侧交互体验

## 为什么重要

音乐生成是多模态 AI 的重要应用方向。Lyria 3 集成到 Gemini App 标志着 AI 创作工具从专业软件走向大众移动应用。对手机端 AIOS 来说：
- 音频生成是比图像/视频更轻量的端侧 AI 任务
- 音乐创作场景对延迟敏感（用户期待实时反馈）
- OS 层的音频处理管线（Audio HAL）需要与 AI 生成管道集成

## 关联

- [[nano-banana-2-imagegen]] — 同为 DeepMind 生成模型，图像生成的端侧经验可复用
- [[gemma4-ondevice]] — Gemma 4 的多模态能力可理解音乐创作意图
- [[gemini-on-device-android]] — Gemini App 是 Lyria 3 的主要载体
- [[audiocraft-mobile]] — Meta 的 AudioCraft 框架在音频生成领域的并行工作
- [[mnn-350]] — 推理引擎对音频生成模型的优化支持
