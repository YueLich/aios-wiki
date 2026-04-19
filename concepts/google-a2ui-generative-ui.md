---
type: concept
tags: [generative-ui, agent-ui, cross-platform, mobile, flutter, a2a, google, 标准协议]
related: [[gui-agent-user-interface]], [[a2a-protocol]], [[mcp-deployment-patterns]], [[secagent-mobile-gui]]
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

# Google A2UI: Agent 驱动的生成式 UI 标准

> Google 发布 A2UI v0.9，一个框架无关的生成式用户界面协议，让 AI Agent 能够动态构建 UI 组件，支持 Web、移动端（Flutter）等多平台。

## 核心问题

当前移动 AI Agent 面临一个根本性瓶颈：**Agent 生成的内容被困在纯文本对话框中**。无论是规划旅行、管理健康数据还是操作应用，Agent 都需要将复杂信息以结构化方式呈现给用户——表格、卡片、表单、图表——而不仅仅是文字流。传统做法是为每个 Agent-应用组合硬编码 UI，这在多 Agent、多场景下不可扩展。

## 方法/架构

A2UI (Agent-to-UI) 定义了一套**协议层**，让 Agent 运行时与 UI 渲染器解耦：

- **共享 Web Core 库**：定义 UI 原语（卡片、列表、表单、图表等）的规范格式
- **多平台渲染器**：
  - React（官方维护）—— Web 前端
  - **Flutter** —— 移动端（Android/iOS）直接渲染
  - Lit —— 轻量 Web Components
  - Angular —— 企业 Web
- **Agent SDK**：Python 已发布，Go 和 Kotlin 开发中。Kotlin SDK 对 Android 端侧 Agent 尤其关键
- **客户端定义函数 (Client-Defined Functions)**：Agent 可以调用客户端注册的回调，实现双向交互
- **客户端-服务端数据同步**：Agent 状态和 UI 状态的自动同步机制

### 生态集成

- **A2A 1.0**：与 Google 的 Agent-to-Agent 协议深度集成，多 Agent 协作时各自可生成独立 UI 片段
- **AG2**：支持 AG2 多 Agent 框架
- **Vercel json-renderer**：Web 部署兼容
- **Oracle Agent Spec**：企业级 Agent 规范

### 示例应用

- **Personal Health Companion**（Rebel App Studio）：健康数据可视化 + Agent 建议
- **Life Goal Simulator**（Very Good Ventures）：长期规划交互式模拟

## 关键洞察

**为什么 Flutter 渲染器是关键**：移动是 Agent 交互的主战场。A2UI 的 Flutter 渲染器意味着 Android/iOS 应用可以通过标准协议接收 Agent 生成的 UI，而不需要为每个 Agent 定制集成。这与 [[secagent-mobile-gui]] 的 GUI 理解能力形成互补——secagent 理解现有界面，A2UI 生成新界面。

**与 MCP 的关系**：[[mcp-deployment-patterns]] 解决的是 Agent 如何调用工具（后端），A2UI 解决的是 Agent 如何呈现结果（前端）。两者是互补的协议层。

**协议 vs 框架的选择**：A2UI 选择了"协议+多渲染器"而非"单一框架"，这降低了采用门槛。但 v0.9 仍是早期版本，Kotlin SDK 未发布意味着 Android 端侧集成还需等待。

## 为什么重要

对手机端 AIOS 的意义：

1. **Agent UI 原生化**：不再需要将 Agent 困在聊天窗口，可以在手机上直接渲染富交互界面
2. **跨应用 Agent 体验**：多个 Agent 可以通过 A2UI 在同一应用中渲染不同 UI 片段
3. **端侧渲染能力**：Flutter 渲染器在设备本地运行，Agent 生成的 UI 描述是轻量 JSON，适合端侧推理场景
4. **与 A2A 协议联动**：多 Agent 协作 + 各自生成 UI = 真正的 Agent 操作系统级体验

## 关联

- [[gui-agent-user-interface]] — GUI Agent 的用户界面设计挑战，A2UI 提供了标准化解法
- [[a2a-protocol]] — Agent-to-Agent 通信协议，A2UI 是其 UI 层补充
- [[mcp-deployment-patterns]] — 工具调用协议，A2UI 是前端呈现层的对应物
- [[secagent-mobile-gui]] — 移动 GUI 理解 Agent，与 A2UI 的 UI 生成能力互补
- [[clawmobile-agentic]] — 原生移动 Agent 架构，A2UI 可作为其 UI 层标准
