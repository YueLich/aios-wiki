---
type: entity
tags: [chrome, browser, ai-mode, search, google, web-ai, side-by-side]
related: [[gemini-nano-chrome137]], [[google-ai-edge-gallery]], [mobile-agent-ecosystem-friction]
sources:
  - url: https://blog.google/products-and-platforms/products/search/ai-mode-chrome/
    title: "A new way to explore the web with AI Mode in Chrome"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Chrome AI Mode: 浏览器端 AI 搜索体验升级

> Google 升级 Chrome 浏览器中的 AI Mode，实现网页与 AI 搜索结果并排显示，消除"标签页跳转"困扰。

## 核心功能

### 并排浏览模式
- 点击 AI Mode 中的链接时，网页在 AI Mode 旁边**并排打开**
- 用户可以同时查看网页内容和 AI 搜索结果
- 无需切换标签页即可提出追问
- 保持搜索上下文连续性

### 解决的核心痛点
传统搜索体验是"标签页跳转"（tab hopping）：在一个标签搜索→点击链接跳到另一个标签→再切回搜索标签继续。这种碎片化体验导致用户丢失上下文和思考线索。

### AI 搜索技能（Skills in Chrome）
- 发现、保存和重新组合 AI 工作流
- 一键重复执行常用 AI 操作
- 将最佳 AI 提示词转化为可复用工具

## 技术架构（推测）

- 利用 Chrome 的侧边栏（Side Panel）API 实现并排渲染
- AI Mode 基于 Gemini 模型驱动搜索理解
- Skills 系统可能基于 Chrome Extensions API + AI 推理

## 为什么重要

对手机端 AIOS 和 Agent 生态：

1. **浏览器即 Agent 平台**：Chrome AI Mode 将浏览器从"网页查看器"升级为"AI 驱动的搜索助手"，这与 Agent 的工具使用范式一致
2. **上下文保持**：并排模式解决了移动 Agent 面临的类似问题——在多任务间保持上下文
3. **技能复用**：Skills in Chrome 的概念与 [[skilldroid-skill-compilation]] 的"编译一次、复用多次"理念一致
4. **端侧推理**：Chrome 持续集成 Gemini Nano（见 [[gemini-nano-chrome137]]），浏览器内 AI 推理能力不断提升
5. **竞争格局**：Google 在浏览器中深度集成 AI，对移动端 Web Agent 的部署模式产生深远影响

## 关联
- [[gemini-nano-chrome137]] — Chrome 137 中的 Gemini Nano 端侧推理
- [[google-ai-edge-gallery]] — Google AI Edge 工具链
- [[mobile-agent-ecosystem-friction]] — 移动 Agent 生态摩擦力
- [[skilldroid-skill-compilation]] — 技能编译与复用概念
