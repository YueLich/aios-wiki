---
type: entity
tags: [Google, Fitbit, wearable, health-AI, edge-ai, on-device]
related: [[wearable-large-sensor-models]], [[visionclaw-wearable-agent]], [[codas-wearable-biomarker]], [[badgex-wearable-llm-learning]]
sources:
  - url: https://9to5google.com/2026/04/19/fitbit-air-google-health/
    title: "Sources: 'Fitbit Air' is a screen-less Whoop competitor debuting with 'Google Health' subscription"
    date: 2026-04-19
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# Google Fitbit Air：无屏健康手环与 Google Health AI 教练

> Google 正在准备一款名为 "Fitbit Air" 的无屏健康手环，以 Whoop 为竞品定位，配合重新品牌的 "Google Health" 订阅服务和 AI 驱动的 "Google Health Coach"。

## 核心信息

- **产品名**：Google Fitbit Air
- **形态**：无屏（screen-less）健康手环，比传统智能手表更轻薄，可全天佩戴
- **品牌策略**：硬件用 Fitbit 品牌，软件和服务用 Google 品牌
- **软件服务**：Fitbit Premium 订阅将重新品牌为 **Google Health**
- **AI 功能**：个性化健康教练（原 "Coach"）将正式命名为 **Google Health Coach**
- **名人背书**：NBA 球星 Stephen Curry 已在佩戴测试
- **命名来源**：Fitbit 之前用 "Air" 命名过 2019 年的 Aria Air 智能体重秤（$49.95），此处 "Air" 指代轻薄设计

## 品牌战略分析

Google 正在将健康功能从 "Fitbit" 品牌迁移到核心 "Google" 品牌：
- **旧**："Fitbit Premium"（Fitbit 品牌下的订阅服务）
- **新**："Google Health"（Google 核心品牌下的健康平台）
- 注意区分："Google Health" 曾是 Google 在健康领域的总称，现在已改名为 "Google for Health"

这解释了 Curry 的预告片以渐变色 'G' logo 结尾、没有 Fitbit 品牌标识的原因。

## 关键洞察

1. **无屏设计 = 边缘计算优先**：没有屏幕意味着所有用户交互都需要通过 AI 算法自动完成（健康分析、建议推送），而非依赖屏幕手动操作。这要求设备具备强大的端侧推理能力。

2. **AI Coach = 端侧个性化 Agent**：Google Health Coach 需要在设备上持续学习用户健康模式、实时分析传感器数据，并给出个性化建议。这是典型的端侧 AI Agent 应用。

3. **品牌统一 = 平台化战略**：从 Fitbit 品牌迁移到 Google 品牌，意味着 Google 将健康 AI 作为其 AI 平台（Gemini 生态）的一部分，而非独立的可穿戴设备业务。

## 为什么重要

对手机端 AI 生态而言，Fitbit Air 代表了一种新的端侧 AI 设备范式：
- **无屏 = 零手动交互**：所有功能由 AI 自动推断和执行
- **全天佩戴 = 持续数据流**：需要低功耗的端侧推理
- **AI Coach = 个性化 Agent**：设备上运行的健康 Agent 需要记忆、推理和行动能力

这与 [[visionclaw-wearable-agent]] 研究的可穿戴 Agent 架构高度吻合，也呼应了 [[wearable-large-sensor-models]] 关于大型传感器模型在穿戴设备上的应用。

## 关联

- [[wearable-large-sensor-models]] — 可穿戴设备上的大型传感器模型，Fitbit Air 的 AI 教练需要类似能力
- [[visionclaw-wearable-agent]] — 可穿戴 Agent 系统架构，与 Fitbit Air 的 AI Coach 概念一致
- [[codas-wearable-biomarker]] — 可穿戴设备生物标志物检测
- [[badgex-wearable-llm-learning]] — 可穿戴设备上的 LLM 学习框架
- [[google-assistant-gemini-transition]] — Google 从 Fitbit 设备中移除 Assistant，为 Gemini 让路
