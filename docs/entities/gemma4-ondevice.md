---
type: entity
tags: [gemma, google, multimodal, on-device, model, android, mlx, llama.cpp]
related: [[on-device-inference]], [[mobile-aios-overview]], [[apple-intelligence]], [[llamacpp-b8811]], [[gemma4-audio-mlx]]
sources:
  - url: https://huggingface.co/blog/gemma4
    title: "Welcome Gemma 4: Frontier multimodal intelligence on device"
    date: 2026-04-02
    reliability: high
  - url: https://blog.google/technology/ai/gemma-4/
    title: "Gemma 4: Google's latest open model"
    date: 2026-04-02
    reliability: high
created: 2026-04-14
updated: 2026-04-16
---

# Gemma 4：端侧前沿多模态智能

> Google DeepMind 发布的多模态开源模型家族，支持图像/文本/音频输入，提供从 2B 到 31B 的多个尺寸，专为端侧部署优化。Apache 2.0 许可。

## 模型家族

| 模型 | 参数量 | 类型 | 上下文窗口 | 音频支持 |
|------|--------|------|-----------|---------|
| Gemma 4 E2B | ~2B | Dense (PLE) | 128K | ✅ |
| Gemma 4 E4B | 4.5B 有效 / 8B 含 embeddings | Dense (PLE) | 128K | ✅ |
| Gemma 4 26B A4B | 26B 总 / 4B 激活 | MoE | 256K | ❌ |
| Gemma 4 31B | 31B | Dense | 256K | ❌ |

所有模型均为 base + instruction-tuned 双版本，Apache 2.0 开源。

## 核心架构创新

### Per-Layer Embeddings (PLE)
Gemma 4 小型模型（E2B、E4B）采用 PLE 技术（源自 Gemma-3n）：
- 每个 token 为每一层生成一个低维专用向量，由 token-identity 和 context-aware 两个信号组合
- 主残差流旁增加并行的低维条件通路
- PLE 维度远小于主隐藏层，以极低参数代价实现逐层特化
- 对多模态输入（图像/音频/视频），PLE 在 soft token 合并前计算，多模态位置使用 pad token ID

**实际效果**：对长上下文生成和端侧使用，在质量和效率之间取得极佳平衡。

### 注意力机制
- **交替局部/全局注意力**：滑动窗口注意力层与全上下文注意力层交替排列
- 小模型滑动窗口 512 tokens，大模型 1024 tokens
- **Dual RoPE**：滑动层使用标准 RoPE，全局层使用裁剪 RoPE，支持更长上下文

### 音频编码器
- USM-style Conformer，与 Gemma-3n 相同基础架构
- 仅 E2B 和 E4B 支持音频输入
- 训练数据包含语音，不包含音乐和非语音声音

## 多模态能力

### GUI 检测与定位
模型原生支持 GUI 元素检测和 bounding box 输出，无需特定指令或语法约束生成：
- 输入图像 + "What's the bounding box for the 'view recipe' element?"
- 模型直接返回 JSON 格式的 bounding box 坐标（基于 1000x1000 坐标系）

### 视频理解
- 小模型支持带音频的视频输入（`load_audio_from_video=True`）
- 大模型支持无音频视频
- E4B 在视频+音频场景下准确识别演唱会内容、歌词主题

### 音频问答
- E4B 可准确转录语音、理解演讲内容
- 测试案例：奥巴马告别演讲音频转录，质量良好

### 多模态 Function Calling
- 支持基于图像内容的工具调用（如识别建筑→调用天气 API）
- 26B/A4B 和 31B 均成功识别泰国寺庙并生成正确的 `get_weather` 工具调用

## 基准测试结果

| 基准 | 31B | 26B/A4B | E4B | E2B | Gemma 3 27B |
|------|-----|---------|-----|-----|-------------|
| **推理与知识** | | | | | |
| MMLU Pro | 领先 | 优秀 | 良好 | — | 对照 |
| AIME 2026 (no tools) | 领先 | 优秀 | — | — | 对照 |
| GPQA Diamond | 领先 | 优秀 | — | — | 对照 |
| **编码** | | | | | |
| LiveCodeBench v6 | 领先 | 优秀 | — | — | 对照 |
| Codeforces ELO | 领先 | 优秀 | — | — | 对照 |
| **视觉** | | | | | |
| MMMU Pro | 领先 | 优秀 | — | — | 对照 |
| MATH-Vision | 领先 | 优秀 | — | — | 对照 |

**关键数据**：31B dense 模型 LMArena 估计分数 1452（纯文本），26B MoE 仅用 4B 激活参数即达 1441。

## 端侧部署支持

### 推理框架覆盖
Gemma 4 发布首日即获得广泛支持：
- **transformers**：原生 `any-to-any` pipeline，`AutoModelForMultimodalLM`
- **llama.cpp**：GGUF 格式，支持各种量化方案
- **MLX**：Apple Silicon 原生支持，详见 [[gemma4-audio-mlx]]
- **transformers.js**：浏览器内推理
- **Mistral.rs**：Rust 推理引擎
- **ONNX**：跨硬件后端，支持边缘设备和浏览器

### 端侧适用性分析
- **E2B (2B)**：最适合手机端，内存占用低，支持音频，适合 Always-on 场景
- **E4B (4.5B)**：手机端可用，多模态能力完整，适合 Agent 场景
- **26B/A4B (4B 激活)**：平板/笔记本端侧可用，MoE 架构天然适合 [[model-quantization]]
- **31B**：需要桌面级 GPU，不适合端侧

## Fine-tuning 支持
- **TRL**：HuggingFace 原生 RLHF/DPO 支持
- **Unsloth Studio**：高效微调工具
- **Vertex AI**：Google Cloud 上的 TRL 微调

## 对手机端 AIOS 的意义

1. **Android 生态多模态基座**：Gemma 4 E2B/E4B 有望成为 [[xiaomi-hyperai]]、三星 Galaxy AI 等系统级 AI 的默认端侧模型
2. **Agent 能力内置**：原生 function calling + GUI 检测 = 端侧 Agent 的理想基座模型
3. **音频智能**：E2B/E4B 的音频支持意味着语音助手可以完全离线运行
4. **PLE 架构示范**：Per-Layer Embeddings 为端侧模型设计提供了新范式，比传统 token embedding 更高效
5. **Apache 2.0 开放生态**：与 [[apple-intelligence]] 的封闭策略形成对比，有利于 Android 生态创新

## 关联

- [[gemma4-audio-mlx]] — Gemma 4 在 Apple Silicon 上的音频处理方案
- [[llamacpp-b8811]] — llama.cpp 对 Gemma 4 的推理支持
- [[apple-intelligence]] — 主要竞争对手的端侧 AI 方案
- [[on-device-inference]] — 端侧推理技术栈
- [[mobile-aios-overview]] — 手机端 AIOS 总体架构
- [[clawmobile-agentic]] — 可基于 Gemma 4 构建的端侧 Agent 系统
- [[mnn-350]] — 竞争/互补的推理框架
