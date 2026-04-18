---
type: concept
tags: [apple, apple-intelligence, 隐私AI, 端侧推理]
related: []
created: 2026-04-18
updated: 2026-04-18
---

# Apple Intelligence

> 概念页面 — 从多个相关页面的 wikilink 引用自动创建

Apple Intelligence 是 Apple 在 2024 年推出的设备端 AI 框架，将大语言模型和生成式 AI 深度集成到 iOS/macOS 系统中。

## 核心特性

- **Private Cloud Compute**: 敏感请求在设备端处理，复杂请求通过加密通道发送到 Apple 自有服务器
- **系统级集成**: 写作工具、图像生成 (Image Playground)、通知摘要、Siri 增强
- **模型架构**: Apple Foundation Models — 端侧 ~3B 参数模型 + 云端更大模型
- **开发框架**: Core ML + Apple Neural Engine 硬件加速

## 端侧推理技术

- **Core ML 优化**: 利用 Apple Silicon 的 Neural Engine 和 GPU
- **适配器模型**: LoRA 适配器实现任务特化，无需完整微调
- **KV-Cache 优化**: 减少端侧内存占用

## 关联

- [[coremltools-9]] — Core ML 工具链
- [[personal-intelligence-google]] — Google 个人智能方案对比
- [[gemma4-ondevice]] — Gemma 4 端侧部署
- [[iphone-17e]] — Apple AI 硬件
- [[ggml-llamacpp-hf]] — 跨平台端侧推理
