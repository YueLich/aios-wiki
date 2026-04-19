---
type: entity
tags: [on-device, multimodal, voice-assistant, snapdragon, gemma, litert, android]
related: [[gemma4-ondevice]], [[huoziime-ondevice-ime]], [[mnn-350]]
sources:
  - url: https://github.com/donge/qiaohu
    title: "Qiaohu: Offline multimodal voice assistant for Snapdragon 8 Gen 2"
    date: 2026-04-09
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Qiaohu: 离线多模态语音助手

> 完全离线的多模态语音助手，在 Snapdragon 8 Gen 2 上运行 Gemma 4 2B——无服务器、无云端、一切在设备上完成。

## 核心问题

如何在手机上实现真正离线的多模态对话系统（语音+视觉），同时保持可接受的响应延迟？

## 技术架构

全链路单 ViewModel，无网络 I/O（首次模型下载后）：

```
麦克风 → VAD (Silero, 16kHz) → LLM (Gemma 4 2B, LiteRT-LM, GPU) → TTS (sherpa-onnx, 22050Hz) → 扬声器
                          ↘ 摄像头 (CameraX) → 多模态输入 ↗
```

### 组件详情

| 组件 | 技术选型 | 说明 |
|------|---------|------|
| LLM | Google LiteRT-LM + Gemma 4 2B | Snapdragon GPU 加速 |
| TTS | sherpa-onnx + matcha-icefall-zh-baker | 中文，22050 Hz |
| VAD | Silero VAD via ONNX Runtime | 16kHz 持续处理 |
| 视觉 | CameraX | 相机帧作为多模态输入 |
| 打断 | Barge-in | 新语音立即中断 TTS 播放 |

### 工作流程

1. SileroVad 持续处理 16kHz 麦克风音频块
2. 检测到语音后，WAV 缓冲区传递给 LlmEngine
3. LlmEngine 封装 LiteRT-LM 的 Engine + Conversation，模型始终通过 `respond_to_user` 工具调用响应（结构化输出）
4. 响应文本按句分割，逐句送入 SherpaOnnxTts
5. AudioPlayer 通过 AudioTrack 播放 PCM——生产者/消费者通道隐藏句间间隙

## 测试环境

- 设备: Vivo V2338A
- 芯片: Snapdragon 8 Gen 2
- 系统: Android 16

## 为什么重要

Qiaohu 证明了在当前硬件上，**完整的多模态对话管线**（VAD + LLM + TTS + 视觉）可以完全离线运行。这打破了"端侧只能做简单任务"的认知——虽然模型只有 2B 参数，但通过合理的管线设计（结构化输出、逐句 TTS、batter-in 打断），用户体验可以接近云端方案。

关键设计决策：使用 LiteRT-LM 而非 MNN/llama.cpp，通过 `respond_to_user` 工具调用强制结构化输出，避免了端侧模型常见的自由格式输出不可控问题。

## 关联

- [[gemma4-ondevice]] — Gemma 4 在端侧的能力基准
- [[huoziime-ondevice-ime]] — 另一个端侧 LLM 应用（输入法个性化）
- [[mnn-350]] — 阿里 MNN 推理框架，LiteRT-LM 的替代方案
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端能力边界分析
