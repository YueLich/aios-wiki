---
type: entity
tags: [google, gemma4, on-device, ios, edge-inference, mobile-ai]
related: [[gemma4-ondevice]], [[gemma4-ondevice]], [[anylanguagemodel-apple]], [[edgeflow-cold-start]]
sources:
  - url: https://simonwillison.net/2026/Apr/6/google-ai-edge-gallery/
    title: "Google AI Edge Gallery — Simon Willison"
    date: 2026-04-06
  - url: https://ai.google.dev/edge/gallery
    title: "Google AI Edge Gallery Official Page"
created: 2026-04-14
---

# Google AI Edge Gallery

Google 官方发布的端侧 AI 模型体验应用，支持在 iPhone 上直接运行 Gemma 4 系列模型。

## 核心功能

- **模型支持**：Gemma 4 E2B（2.54GB）和 E4B，以及部分 Gemma 3 家族模型
- **多模态能力**：支持图像问答（Ask questions about images）和音频转录（最长30秒）
- **Skills 工具调用演示**：内含 8 个交互式 widget 展示端侧 tool calling 能力：
  - interactive-map、kitchen-adventure、calculate-hash、text-spinner
  - mood-tracker、mnemonic-password、query-wikipedia、qr-code
- **性能**：E2B 模型在 iPhone 上运行速度快，实际可用

## 为什么重要

1. **首个模型厂商官方端侧应用**：这是 Google 首次为 Gemma 模型发布官方 iPhone 应用，标志着模型厂商从「发布模型」走向「发布端侧体验」
2. **端侧 tool calling 验证**：Skills 演示展示了端侧模型的 function calling 能力，这是 [[edgeflow-cold-start|端侧 Agent]] 的基础能力
3. **多模态端侧闭环**：视觉+音频+文本在同一应用中完成，验证了 [[gemma4-ondevice|Gemma 4 端侧多模态]] 的实用性
4. **与 Apple 生态的竞合**：在 iPhone 上运行 Google 模型（而非 [[anylanguagemodel-apple|Apple 自有方案]]），展示了跨平台端侧 AI 的可能性

## 局限

- 对话记录是临时的（ephemeral），没有持久化日志
- Skills 演示的源码不可见
- Skills 演示在追加 prompt 时偶发冻结

## 与 Wiki 其他页面的关系

- 作为 [[gemma4-ondevice]] 的官方体验入口，补充了模型从发布到用户体验的最后一环
- 与 [[anylanguagemodel-apple]] 形成对比：Google 选择自建应用 vs Apple 选择开放 API
- 验证了 [[edgeflow-cold-start]] 所述的冷启动优化在实际应用中的效果
