---
type: entity
tags: [model, multimodal, on-device, google, gemma, vision]
related: [[gemma4-audio-mlx]], [[gemma-3-google]], [[coremltools-9]]
sources:
  - https://huggingface.co/blog/gemma4
  - https://simonwillison.net/2026/Apr/13/gemma-4-audio-with-mlx/
created: 2026-04-14
---

# Gemma 4

Google 最新的端侧多模态模型，支持视觉、文本和音频理解。

## 核心信息
- **发布方**：[[google]] via [[huggingface]]
- **定位**：Frontier multimodal intelligence on device（端侧前沿多模态智能）
- **特色**：可在手机等边缘设备上运行的多模态大模型
- **音频能力**：Gemma 4 E2B 模型（10.28GB）支持音频转录，可通过 [[mlx-vlm]] 在 macOS 上本地运行

## 为什么重要
Gemma 4 代表了 Google 在端侧 AI 的重要布局。不同于依赖云端 API 的方案，Gemma 4 直接在设备上运行多模态推理，意味着：
1. **隐私保护**：敏感数据不离开设备
2. **离线可用**：无需网络连接即可进行视觉和语音理解
3. **低延迟**：本地推理避免网络往返延迟
4. **Apple Silicon 优化**：通过 [[mlx]] 框架在 Mac 上高效运行

这与 [[apple-intelligence]] 的端侧策略形成直接竞争，也标志着开源端侧多模态模型进入实用阶段。
