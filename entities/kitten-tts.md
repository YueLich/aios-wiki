---
type: entity
tags: [tts, on-device, speech, lightweight, cpu, text-to-speech, 语音合成, 端侧推理]
related: [[on-device-streaming-asr-microsoft]], [[huoziime-ondevice-llm-input-method]], [[xybrid-llm-asr-tts]]
sources:
  - url: https://github.com/KittenML/KittenTTS
    title: "Kitten TTS - Open-source lightweight TTS"
    date: 2026-04-19
    reliability: high
  - url: https://huggingface.co/KittenML/kitten-tts-mini-0.8
    title: "Kitten TTS models on HuggingFace"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Kitten TTS v0.8: 超轻量级端侧语音合成

> 开源、ONNX驱动的TTS库，最小模型仅15M参数/25MB，纯CPU即可运行，支持8种语音和24kHz输出。GitHub 1003★。

## 核心信息

Kitten TTS是KittenML团队开发的开源轻量级文本转语音库，专注于端侧部署场景。v0.8版本提供了三个规模的模型：

| 模型 | 参数量 | 大小（int8） | 适用场景 |
|------|--------|-------------|---------|
| kitten-tts-nano | 15M | 25 MB | 极限边缘设备、IoT |
| kitten-tts-micro | 40M | 41 MB | 手机端常用 |
| kitten-tts-mini | 80M | 80 MB | 最佳质量，仍可CPU运行 |

### 核心特性
- **纯CPU推理**：基于ONNX，无需GPU
- **8种内置语音**：Bella, Jasper, Luna, Bruno, Rosie, Hugo, Kiki, Leo
- **可调节语速**：通过speed参数控制播放速率
- **内置文本预处理**：自动处理数字、货币、单位等
- **24kHz输出**：标准采样率的高质量音频
- **Apache 2.0许可证**：可商用

### 技术架构
- 基于ONNX Runtime推理
- 模型量化（int8）大幅减小体积
- 支持HuggingFace Spaces在线Demo

## 为什么重要

**端侧TTS的最后一块拼图**：在端侧AI生态中，ASR（语音识别）已有[[on-device-streaming-asr-microsoft]]等成熟方案，LLM推理有[[gemma4-ondevice]]等选择，但TTS一直是缺失环节。Kitten TTS的25MB int8模型填补了这个空白，使得完整的端侧语音交互成为可能（ASR → LLM推理 → TTS）。

**与[[xybrid-llm-asr-tts]]的互补**：xybrid展示了在同一个应用中集成LLM+ASR+TTS的能力，但需要Google的模型。Kitten TTS提供了更轻量的开源替代。

**部署门槛极低**：25MB的模型大小意味着可以嵌入任何移动应用，甚至网页端（通过ONNX.js）。与需要数百MB的Whisper或ChatTTS相比，Kitten TTS是真正的"零依赖"方案。

## 关联
- [[on-device-streaming-asr-microsoft]] — 端侧语音识别，与TTS配合构成完整语音交互
- [[huoziime-ondevice-llm-input-method]] — 同为端侧文本处理，但方向不同
- [[xybrid-llm-asr-tts]] — 端侧多模态推理集成（LLM+ASR+TTS）
- [[apple-intelligence]] — Apple生态的端侧AI方案也包含TTS能力
