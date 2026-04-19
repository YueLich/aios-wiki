---
type: concept
tags: [ai-agent, ui-generation, generative-ui, mobile, web, cross-platform, google, standard]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[agent-persistent-identity]], [[clawmobile-agentic]]
sources:
  - url: https://the-decoder.com/google-launches-generative-ui-standard-for-ai-agents/
    title: "Google launches generative UI standard for AI agents"
    date: 2026-04-19
    reliability: high
  - url: https://a2ui.org
    title: "A2UI Official Documentation"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Google A2UI 0.9 — AI Agent 生成式 UI 标准

> Google 发布的框架无关标准，让 AI Agent 动态生成 UI 元素，跨 Web、移动端和多平台复用应用现有组件。

## 核心问题

传统 AI Agent 与用户界面的交互方式存在根本性瓶颈：Agent 通常只能通过文本对话或预定义的 API 调用与用户交互，无法直接构建和操控用户界面。这意味着每个应用都需要为 AI 集成编写大量定制代码，且不同平台（Web、iOS、Android）需要重复开发。A2UI（Agent-to-UI）标准旨在解决这一问题——让 Agent 能够动态"看到"应用的可用组件，并即时生成对应的用户界面。

## 方法/架构

A2UI 0.9 的核心架构包含以下组件：

**协议层**：
- **框架无关设计**：A2UI 定义了一套标准化的 UI 组件描述协议，不绑定任何特定前端框架
- **组件发现机制**：应用向 Agent 暴露其可用的 UI 组件库，Agent 根据上下文动态选择和组合

**渲染层**：
- **共享 Web 核心库**：提供基础渲染能力
- **官方 React 渲染器**：针对 React 生态的优化实现
- **Flutter / Lit / Angular 渲染器**：覆盖主流跨平台和 Web 框架

**Agent SDK**：
- **Python SDK**（首发）：`pip install a2ui-agent`，用于 Agent 端开发
- **Go SDK**（开发中）：面向高性能后端场景
- **Kotlin SDK**（开发中）：面向 Android 原生开发

**核心特性**：
- **客户端定义函数（Client-Defined Functions）**：应用可以在客户端注册可被 Agent 调用的函数
- **客户端-服务器数据同步**：Agent 生成的 UI 状态可与后端实时同步
- **改进的错误处理**：Agent UI 生成失败时的降级策略

**生态集成**：
- **AG2**：与 AG2 多 Agent 框架集成
- **A2A 1.0**：遵循 Google 的 Agent-to-Agent 通信协议
- **Vercel json-renderer**：与 Vercel 前端工具链打通
- **Oracle Agent Spec**：企业级 Agent 规范兼容

## 实验结果/关键数据

A2UI 0.9 目前处于早期阶段（版本号 0.9 表明尚未稳定）。已有示例应用：

- **Personal Health Companion**（Rebel App Studio）：Agent 动态生成健康数据可视化 UI，根据用户输入实时调整界面布局和数据展示方式
- **Life Goal Simulator**（Very Good Ventures）：Agent 根据用户目标生成交互式模拟界面，支持多步骤表单和动态结果展示

跨平台支持矩阵：

| 平台 | 渲染器状态 | SDK 状态 |
|------|-----------|---------|
| Web (React) | ✅ 官方 | — |
| Web (Angular) | ✅ 更新 | — |
| Web (Lit) | ✅ 更新 | — |
| Flutter | ✅ 更新 | — |
| Android (Kotlin) | — | 🔧 开发中 |
| iOS | — | ❌ 未公布 |
| Go 后端 | — | 🔧 开发中 |

## 关键洞察

**为什么 A2UI 是移动 AIOS 的关键基础设施**：

1. **Agent UI 原生化**：当前手机端 Agent（如 Google Gemini on Android、Apple Intelligence）的 UI 交互仍受限于固定的聊天窗口或预定义的卡片。A2UI 打破了这一限制——Agent 可以生成任意复杂的交互界面，就像人类开发者编写 UI 一样。这对 [[clawmobile-agentic]] 等原生 Agent 系统的 UI 层有直接影响。

2. **跨平台一致性**：A2UI 的框架无关设计意味着一个 Agent 可以在 Web、Android、iOS 上生成一致的 UI 体验。这解决了当前移动 AI 生态中"每个平台一套 UI"的碎片化问题。

3. **与 GUI Agent 的互补关系**：[[secagent-mobile-gui]] 等 GUI Agent 项目专注于"理解"现有 UI（屏幕理解、OCR），而 A2UI 专注于"生成"新 UI。两者的结合将形成完整的 Agent-UI 闭环：理解 → 决策 → 生成 → 执行。

4. **A2A 协议集成**：A2UI 与 Google A2A 1.0 协议的集成意味着多 Agent 系统可以协作生成复杂 UI。这对移动设备上的多 Agent 场景（如个人助理 + 健康 Agent + 日程 Agent 协作）有重要价值。

5. **Kotlin SDK 的战略意义**：Kotlin SDK 的开发中状态表明 Google 正在将 A2UI 深度集成到 Android 生态。结合 Android 17 的 Agent Mode 特性，这可能是 Android 原生 Agent UI 框架的基础。

## 为什么重要

A2UI 代表了 AI Agent 交互范式从"对话式"向"生成式 UI"的转变。对移动 AIOS 生态而言：

- **用户体验革命**：Agent 不再局限于文本对话，可以生成富交互界面，大幅提升移动端 AI 可用性
- **开发效率提升**：开发者只需定义组件库，Agent 自动组合生成 UI，减少手动编码
- **平台锁定减弱**：框架无关设计让 Agent 应用更容易跨平台部署
- **新交互模式**：从"用户找功能"到"Agent 生成功能界面"，重新定义移动端人机交互

## 关联

- [[secagent-mobile-gui]] — A2UI 生成 UI，GUI Agent 理解 UI，两者互补形成闭环
- [[pspa-bench-gui-agent]] — A2UI 生成的 UI 需要新的 benchmark 评估其可用性
- [[agent-persistent-identity]] — Agent 生成的 UI 风格应反映 Agent 的持久化身份
- [[clawmobile-agentic]] — ClawMobile 的原生 Agent 架构可集成 A2UI 作为 UI 层
- [[a2a-protocol]] — A2UI 依赖 A2A 1.0 进行多 Agent 间的 UI 协作
