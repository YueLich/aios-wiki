---
type: concept
tags: [react-native, cross-platform, on-device, llm, llama.cpp, gguf, 推理框架]
related: [[anylanguagemodel-apple]], [[gemma4-ondevice]], [[kv-cache-quantization-ondevice]]
sources:
  - "[HuggingFace Blog] LLM Inference on Edge: A Fun and Easy Guide to run LLMs via React Native on your Phone!"
  - URL: https://huggingface.co/blog/llm-inference-on-edge
created: 2026-04-14
---

# React Native 端侧 LLM 推理

## 概念定义

通过 React Native + llama.rn（llama.cpp 的 React Native 绑定）实现跨平台手机端 LLM 推理的技术方案。用户可以从 HuggingFace Hub 下载 GGUF 格式模型，在手机本地运行对话式 AI。

## 实践路径

1. 选择合适大小的模型（推荐 1.5B 参数量级，如 DeepSeek R1 Distil Qwen 2.5）
2. 使用 GGUF 量化格式（平衡精度和体积）
3. 通过 llama.rn 加载模型，实现本地推理
4. 数据完全本地处理，确保隐私

## 为什么重要

**降低门槛**：React Native 是最流行的跨平台移动框架之一。将端侧 LLM 推理带入 React Native 生态，意味着数百万 Web/JS 开发者可以轻松集成 AI 功能。

**隐私优势**：所有推理在设备上完成，无需联网——这对敏感场景（医疗、金融、个人助手）至关重要。

**技术成熟度**：使用 llama.cpp + GGUF 作为推理后端，说明端侧推理的工具链已经足够成熟，可以被非 ML 专业开发者使用。

## 与手机端 AIOS 的关联

这代表了端侧 AI 从"研究可用"到"工程可用"的转变。与 [[anylanguagemodel-apple]] 在 Apple 生态的统一 API 遥相呼应，React Native 方案覆盖了跨平台开发需求。结合 [[kv-cache-quantization-ondevice]] 等优化技术，可以在手机上运行越来越大的模型。

## 相关概念

- [[anylanguagemodel-apple]] — Apple 平台统一 API
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化优化
- [[gemma4-ondevice]] — 端侧多模态模型
