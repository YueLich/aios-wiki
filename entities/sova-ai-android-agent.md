---
type: entity
tags: [android, mobile-agent, accessibility-api, on-device, ai-assistant, gui-agent, agentic]
related: [[clawmobile-agentic]], [[pspa-bench-gui-agent]], [[gui-agent-privacy]], [[knowu-bench-mobile-agent-eval]]
sources:
  - url: https://ayconic.io/sova
    title: "Sova AI - AI Assistant for Your Phone"
    date: 2026-04-17
    reliability: medium
  - url: https://news.ycombinator.com/item?id=47613614
    title: "Google banned our mobile AI agent app for doing what Gemini should do, but doesn't"
    date: 2026-04-17
    reliability: medium
created: 2026-04-19
updated: 2026-04-19
---

# Sova AI

> Android原生Agent助手，通过Accessibility API操控手机App执行任务。无需root/ADB/PC。被Google Play下架。开源BYOK模式。

## 核心问题

内置AI助手（Gemini等）虽然深度集成OS，但面对"帮我叫Uber去机场"或"给朋友群发消息说我迟到"等真实任务时，只会给出网页搜索结果或打开App的按钮——不会真正执行操作。

## 方法/架构

**技术路径**：
- **Accessibility API**：读取屏幕UI节点树，模拟人类点击/滚动/输入
- **纯Kotlin原生实现**：无需PC/Appium/Shizuku/ADB
- **多模型支持**：OpenAI、Gemini、Anthropic、Deepseek等云端模型 + 计划支持Ollama/LM Studio本地模型
- **BYOK模式**：自带API Key，引擎100%免费

**关键挑战**：
- 将LLM输出转换为精确的X/Y坐标（动态Android屏幕 + 千种设备分辨率）
- 不同模型提供商的图片resize差异
- 非100%准确率，需要持续优化

**Google Play下架事件**：
因使用Accessibility API进行"通用自动化"（映射和点击其他App），被Google Play拒绝。团队自行托管APK。讽刺的是，他们构建的正是Gemini承诺但未实现的Agent能力。

## 为什么重要

- 展示了端侧Agent的实际落地形态：Accessibility API + LLM = App操控Agent
- 揭示了平台政策（Google Play审核）对Agent创新的阻碍
- BYOK模式可能成为端侧AI Agent的商业模式之一
- 与[[clawmobile-agentic]]的原生架构理念呼应：Agent需要真正操控App而非仅仅建议

## 关联
- [[clawmobile-agentic]] — 原生Agent系统架构
- [[pspa-bench-gui-agent]] — GUI Agent基准
- [[gui-agent-privacy]] — Agent隐私保护（Accessibility API是敏感接口）
- [[knowu-bench-mobile-agent-eval]] — 个性化Agent评估
