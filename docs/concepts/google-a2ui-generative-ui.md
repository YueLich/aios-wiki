---
type: concept
tags: [agent-ui, generative-ui, mobile-agent, gui-agent, a2a-protocol, google]
related: [[clawmobile-agentic]], [[secagent-mobile-gui]], [[pspa-bench-gui-agent]]
sources:
  - url: https://the-decoder.com/google-launches-generative-ui-standard-for-ai-agents/
    title: "Google launches generative UI standard for AI agents"
    date: 2026-04-19
    reliability: medium
  - url: https://a2ui.org
    title: "A2UI Documentation"
    date: 2026-04-19
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Google A2UI: AI Agent 的生成式 UI 标准

> Google 发布 A2UI v0.9，一个框架无关的生成式用户界面标准。让 AI Agent 能够实时动态构建 UI 元素，支持 Web、Flutter、React、Angular 等多平台。

## 核心问题

当前 AI Agent 与用户的交互主要依赖**纯文本对话**。但很多场景需要**结构化 UI**：
- 数据可视化（图表、表格）
- 表单输入（需要用户填写的多字段）
- 多步骤流程（引导式操作）

**问题**：Agent 如何动态生成合适的 UI？每个平台（Web/Android/iOS）的 UI 框架不同，Agent 需要一种统一的方式来描述和生成界面元素。

## 方法/架构

### A2UI 协议设计

A2UI v0.9 是一个**框架无关**的协议层：

1. **共享 Web Core 库**：核心协议定义和解析逻辑
2. **多平台渲染器**：
   - React（官方维护）
   - Flutter（移动端）
   - Lit（轻量 Web Components）
   - Angular（企业 Web）
3. **Agent SDK**：Python SDK（Go 和 Kotlin 即将推出），让 Agent 开发者生成 A2UI 兼容的 UI 描述

### 关键能力
- **客户端定义函数（Client-defined functions）**：UI 元素可以绑定本地执行逻辑
- **客户端-服务端数据同步**：Agent 端和设备端状态实时同步
- **组件复用**：从应用已有的 UI 组件库中拉取，而非从零生成
- **错误处理**：改进的 UI 渲染失败恢复机制

### 生态集成
- AG2（AutoGen）集成
- A2A 1.0 协议兼容
- Vercel json-renderer 集成
- Oracle Agent Spec 兼容
- 早期应用：Personal Health Companion、Life Goal Simulator

## 实验/应用

目前 v0.9 为初始版本，尚无大规模基准测试。但已有示范应用：
- **Personal Health Companion**（Rebel App Studio）：Agent 生成健康数据可视化 UI
- **Life Goal Simulator**（Very Good Ventures）：交互式目标规划界面

## 关键洞察

1. **生成式 UI 是 Agent 成熟的关键一步**：从"聊天机器人"到"真正助手"的跨越，需要 Agent 能主动构建合适的交互界面，而非仅输出文本
2. **对手机端 GUI Agent 的意义**：现有 GUI Agent（如 [[secagent-mobile-gui]]）专注于理解和操作已有 UI。A2UI 开辟了反向路径——Agent 生成新 UI。两者结合可以形成完整的"感知+生成"闭环
3. **Flutter 支持是移动端杀手锏**：Google 在 A2UI 中同时提供 Flutter 渲染器，意味着 Android/iOS 原生应用可以直接集成 Agent 生成的 UI 组件

## 为什么重要

- **GUI Agent 范式拓展**：当前手机端 GUI Agent（DroidRun、AppAgent、VisionClaw）都假设 UI 是固定的、需要被"理解"的。A2UI 让 Agent 成为 UI 的**创造者**
- **跨平台统一**：一套 A2UI 描述可以同时渲染为 Web/Android/iOS，减少 Agent 开发者的碎片化工作
- **与 A2A 协议协同**：A2UI 兼容 A2A 1.0，意味着多 Agent 系统中，Agent 可以为其他 Agent 生成 UI——打开了"Agent 为 Agent 构建界面"的可能

## 关联

- [[secagent-mobile-gui]] — SecAgent 感知 GUI，A2UI 生成 GUI，形成完整闭环
- [[pspa-bench-gui-agent]] — PSPA-Bench 测试 Agent 操作 UI 的能力，A2UI 改变 UI 来源
- [[clawmobile-agentic]] — 原生 Agent 架构可集成 A2UI 作为动态 UI 生成层
- [[mana-mobile-ad-detection]] — 广告检测 Agent 可用 A2UI 生成替代界面
- [[visionclaw-wearable-agent]] — 穿戴设备 Agent 的 UI 挑战可借助 A2UI 简化
