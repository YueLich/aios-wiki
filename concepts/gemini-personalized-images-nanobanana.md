---
type: concept
tags: [gemini, nano-banana, personalized-ai, google-photos, on-device, mobile-ai, multimodal]
related: [[gemma4-ondevice]], [[gemini-31-flash-tts]], [[secagent-mobile-gui]]
sources:
  - url: https://blog.google/innovation-and-ai/products/gemini-app/personal-intelligence-nano-banana/
    title: "New ways to create personalized images in the Gemini app"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Gemini 个性化图像生成 (Nano Banana 2)

> Nano Banana 2 结合 Google Photos 个人上下文，让 Gemini 应用生成反映用户独特生活的个性化图像。

## 核心问题

传统 AI 图像生成需要用户编写详细的 prompt 来描述想要的画面。对于涉及自己或亲友的场景，用户需要反复调整才能得到满意结果。Google 的解决方案是让 Gemini 利用用户已有的数据（Google Photos、个人偏好）来理解"你想要什么样的图"，而不是依赖冗长的文字描述。

## 方法与架构

### Personal Intelligence 框架

Gemini 的"Personal Intelligence"是一个跨应用上下文理解系统：

1. **上下文整合**：连接 Google Photos、用户兴趣偏好等个人数据源
2. **免手动上传**：不需要用户每次上传参考照片，Gemini 自动从已连接账户中提取相关上下文
3. **自然语言触发**：简单说 "画一张我在海边的照片"，AI 自动选取合适的参考照片
4. **迭代优化**：结果不满意时可以更换参考照片或调整风格

### Nano Banana 2 模型

- Nano Banana 是 Google 的轻量级图像生成模型
- Nano Banana 2 是第二代，改进了个性化能力
- 集成到 Gemini App 中（而非独立产品）
- 支持 U.S. Google AI Plus/Pro/Ultra 订阅用户

### 隐私保护

- Gemini 不使用用户的私有照片库训练模型
- 用户保留完全创意控制权（可随时更换参考照片）
- 仅在用户明确请求时访问 Google Photos

## 关键洞察

### "个性化上下文"是端侧 AI 的核心竞争力

1. **云端通用模型 vs 端侧个人模型**：Nano Banana 2 展示了一种混合模式——模型本身可能是云端的，但个人上下文（照片库、偏好）是本地/私有的
2. **数据飞轮效应**：用户在 Google Photos 中积累的照片越多，个性化效果越好，形成正向循环
3. **与 Apple Intelligence 的竞争**：Apple 的 Personal Intelligence 也走类似路线，但整合深度不同

### 对手机端 AIOS 的意义

- **端侧上下文理解**：手机是个人数据最丰富的设备，谁能最好地利用这些数据，谁就掌握了 AI 体验的制高点
- **多模态融合**：文本理解 + 图像生成 + 个人照片的三合一，是端侧多模态 AI 的典型场景
- **从通用到个人**：AI 的下一个阶段不是更聪明的通用模型，而是更懂你个人的上下文感知系统

## 关联

- [[gemma4-ondevice]] — Gemma 4 在 Android 端的端侧部署
- [[gemini-31-flash-tts]] — Gemini 3.1 的语音能力扩展
- [[secagent-mobile-gui]] — 移动端 Agent 的屏幕/上下文感知
- [[agent-persistent-identity]] — Agent 如何理解用户身份和偏好
