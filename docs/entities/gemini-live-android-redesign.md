---
type: entity
tags: [Google, Gemini, mobile-ai, UX, Android, agent, voice-assistant]
related: [[google-assistant-gemini-transition]], [[gemini-31-flash-live]], [[personal-intelligence-google]], [[gemini-31-flash-tts]]
sources:
  - url: https://9to5google.com/2026/04/18/gemini-live-redesign-android/
    title: "Gemini overlay and Gemini Live start rolling out big Android redesign"
    date: 2026-04-07
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Gemini Live Android 重塑：从全屏应用到浮动叠加层

> Google 为 Android 上的 Gemini overlay 和 Gemini Live 推出重大视觉重新设计，将全屏交互替换为浮动叠加层，并统一了附件和工具菜单。

## 核心变化

### Gemini Overlay 重新设计

之前的 overlay 使用横跨屏幕的药丸形输入栏。新设计：
- 药丸变窄，"Ask Gemini" 文字更大
- 麦克风图标切换为描边风格
- 点击 "+" 弹出底部面板（bottom sheet）
- **统一附件和工具菜单**：之前分离的两个菜单合并为一个
- 顶部轮播：Photos、Camera、Files、Drive、Notebooks（使用大圆角方块）
- 下方功能行：Create image、Create video、Create music、Canvas、Deep research、Guided learning、**Personal Intelligence**（开关）

### Gemini Live 浮动界面

最大的变化：**全屏界面被浮动叠加层取代**。
- 波形图居中，两侧是屏幕共享和键盘按钮
- 右上角有字幕按钮
- 开始使用手机导航后，Live overlay 缩小为比之前更小的圆圈
- 在完整 Gemini app 中启动 Live 时也使用新的浮动界面，主页出现在下方

### 技术细节

- 出现在 Google app beta 17.3 版本
- 稳定版尚未上线
- Google 也在网页版测试统一设计

## 关键洞察

1. **从"应用中心"到"系统级叠加"**：Gemini Live 从全屏应用变成浮动叠加层，意味着 Google 将 AI 助手定位为**系统级服务**而非独立应用。这与 Android 的 "AI Core" 架构方向一致。

2. **Personal Intelligence 开关**：在工具菜单中直接暴露 Personal Intelligence 开关，表明 Google 正在将个性化 AI 推理作为用户可控功能，而非后台隐式行为。

3. **创作工具集成**：Create image/video/music 的直接入口表明 Gemini 不仅是问答工具，而是**多模态创作平台**在移动端的呈现。

## 为什么重要

这一 UX 重塑反映了移动端 AI 助手从"独立应用"到"系统级基础设施"的演进趋势。浮动叠加层的设计意味着 AI 能力需要：
- 更低的端侧推理延迟（[[edgeflow-cold-start]]）
- 更好的端云协同（[[experimental-hybrid-inference-android]]）
- 多模态理解能力（[[personal-intelligence-google]]）

## 关联

- [[google-assistant-gemini-transition]] — 这次 UX 重塑是 Assistant → Gemini 迁移的具体体现
- [[gemini-31-flash-live]] — Gemini Live 使用的底层模型
- [[personal-intelligence-google]] — Personal Intelligence 功能的详细分析
- [[gemini-31-flash-tts]] — Gemini Live 语音输出使用的 TTS 模型
- [[experimental-hybrid-inference-android]] — 支撑移动端 Gemini 推理的混合推理架构
