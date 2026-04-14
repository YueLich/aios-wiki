---
type: concept
tags: [audio, mlx, on-device, speech-to-text, macos, apple-silicon, 其他]
related: [[gemma-4-google]], [[mlx-framework]], [[whisper]], [[apple-silicon]]
sources:
  - https://simonwillison.net/2026/Apr/13/gemma-4-audio-with-mlx/
created: 2026-04-14
---

# Gemma 4 端侧音频处理（MLX）

在 Apple Silicon 设备上使用 Gemma 4 E2B 模型进行本地音频转录的方案。

## 技术实现
通过 [[mlx-vlm]] 框架在 macOS 上本地运行 Gemma 4 E2B 模型（10.28GB）：

```bash
uv run --python 3.13 --with mlx_vlm --with torchvision --with gradio \
  mlx_vlm.generate \
  --model google/gemma-4-e2b-it \
  --audio file.wav \
  --prompt "Transcribe this audio" \
  --max-tokens 500 --temperature 1.0
```

## 实际效果
- 在 14 秒 WAV 文件上测试，转录质量良好
- 存在少量误识别（如 "This right here" 被识别为 "This front here"）
- 整体可用级别，适合离线转录场景

## 为什么重要
这是[[端侧音频智能]]的一个重要里程碑：
1. **全离线**：音频数据完全不离开设备
2. **多模态统一**：同一模型处理视觉、文本和音频，无需 [[whisper]] 等专用模型
3. **MLX 优化**：Apple Silicon 原生推理框架，充分发挥 M 系列芯片性能
4. **开发者友好**：一条 uv 命令即可运行，降低端侧 AI 使用门槛

对 [[mobile-aios]] 而言，这展示了端侧多模态模型已从"实验室演示"进入"开发者可用"阶段。
