---
type: entity
tags: [tts, gemini, google, 多模态, 语音合成, 端侧推理]
related: [[gemma4-ondevice]], [[gemini-flash-live]], [[gemma4-audio-mlx]], [[anylanguagemodel-apple]]
sources:
  - url: https://the-decoder.com/google-ships-its-most-expressive-gemini-3-1-text-to-speech-model-yet-with-70-language-support/
    title: "Google ships its most expressive Gemini 3.1 text-to-speech model yet with 70+ language support"
    date: 2026-04-15
    reliability: medium
  - url: https://blog.google/technology/ai/
    title: "Google AI Blog"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Gemini 3.1 Flash TTS

> Google基于Gemini 3.1 Flash推出新一代文本转语音模型，支持70+语言，引入Audio Tags实现风格/语速/音调精确控制，在质量价格比上击败ElevenLabs v3。

## 核心能力

**Audio Tags — 精确语音控制**
- 简单文本命令控制语音的风格（style）、语速（tempo）、音调（tone）、口音（accent）
- 支持多说话人对话生成
- 开发者无需复杂SSML标记即可实现专业级语音效果

**多语言支持**
- 70+语言覆盖
- 统一模型处理多语言混合输入
- 对[[anylanguagemodel-apple]]的Apple多语言模型形成直接竞争

## 性能与排名

在Artificial Analysis排名中：
- Elo评分：1,211
- 质量价格比维度表现突出
- **质量超越ElevenLabs v3**，仅次于Inworld 1.5 Max
- 排名前列的TTS模型之一

## 定价

| 层级 | 文本输入 | 音频输出 | 备注 |
|------|----------|----------|------|
| 免费层 | 免费 | 免费 | Google使用数据改进产品 |
| 付费层 | $1.00/百万token | $20.00/百万token | 不使用数据 |
| 批处理模式 | $0.50/百万token | $10.00/百万token | 半价 |

## 可用渠道

- **Gemini API**（Preview阶段）
- **Vertex AI**（企业用户）
- **Google Vids**（Workspace用户）
- **Google AI Studio**（免费试用）
- 所有生成音频均带**SynthID水印**

## 对移动AIOS的意义

**端侧TTS竞争格局**：Gemini 3.1 Flash TTS目前是云端API服务，但其轻量级架构暗示了端侧部署的潜力。Google在[[gemma4-ondevice]]等端侧模型上的策略一贯是"先云端验证，再端侧压缩"。

**多语言Agent语音输出**：70+语言支持对全球化移动Agent场景（如[[clawmobile-agentic]]的原生Agent）至关重要。Audio Tags功能使Agent能根据上下文调整语音风格，提升用户体验。

**质量价格比优势**：$20/百万token的音频输出价格具有竞争力，对移动端集成API调用友好。

## 为什么重要

TTS是移动AIOS Agent系统的输出通道。[[gemini-flash-live]]的实时对话能力需要高质量TTS配合。Gemini 3.1 Flash TTS的Audio Tags功能为Agent语音输出提供了前所未有的控制粒度——Agent可以根据任务紧急程度调整语速、根据用户情绪调整语调，实现更自然的人机交互。

## 关联
- [[gemma4-ondevice]] — Google端侧模型生态
- [[gemini-flash-live]] — Gemini实时对话能力
- [[gemma4-audio-mlx]] — Gemma 4音频处理能力
- [[anylanguagemodel-apple]] — Apple多语言模型对比
- [[clawmobile-agentic]] — 原生Agent语音交互
- [[mobile-agent-ecosystem-friction]] — 移动Agent交互体验
