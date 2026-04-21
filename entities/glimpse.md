---
type: entity
tags: [on-device, ai, macos, markdown, local-inference, privacy]
related: [[edge-inference-memory-pressure]], [[ggml-llamacpp-hf]], [[mnn-350]]
sources:
  - url: https://apps.apple.com/us/app/glimpse-markdown-viewer/id6761304904?mt=12
    title: "Glimpse - App Store"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Glimpse: macOS 端侧 AI Markdown 阅读器

> 原生 macOS 应用，集成端侧 AI 实现文档秒级摘要，支持六种渲染主题、演示模式和内联编辑

## 核心问题

用户在阅读长篇 Markdown 文档时需要快速理解内容要点，但现有工具要么依赖云端 AI（隐私风险），要么没有智能摘要功能。同时，macOS 缺乏高质量的原生 Markdown 阅读器。

## 功能特性

- **端侧 AI 摘要**：所有 AI 推理在本地完成，文档数据不离开设备
- **六种渲染主题**：满足不同阅读偏好
- **演示模式**：将 Markdown 文档转为幻灯片展示
- **内联编辑**：直接在阅读器中编辑 Markdown
- **PDF/HTML 导出**：多格式输出

**应用规模**：6 MB 轻量级，App Store 可下载，免费试用 14 天

## 为什么重要

Glimpse 展示了端侧 AI 在日常工具中的实际应用模式：

1. **隐私优先**：所有推理本地完成，用户无需上传文档到云端
2. **极致轻量**：6MB 包大小意味着模型经过高度压缩/量化
3. **产品化路径**：从 LLM 到实际可用的消费者产品，展示了端侧 AI 的商业化可能性
4. **macOS 生态**：可能基于 Core ML + Apple Silicon 优化，是 Apple 端侧推理栈的实践案例

对于手机端 AIOS 研究，Glimpse 提供了参考价值——如何将端侧 AI 无缝集成到轻量级应用中。

## 关联

- [[edge-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[ggml-llamacpp-hf]] — 可能使用的底层推理引擎
- [[mnn-350]] — 另一个端侧推理框架的选择
- [[coremltools-9]] — Apple 端侧推理工具链
