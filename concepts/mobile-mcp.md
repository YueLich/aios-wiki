---
type: concept
tags: [mcp, android, tool-discovery, agent, intent-framework, 动态发现, 工具调用]
related: [[on-device-vs-cloud-agentic-tool-calling]], [[clawmobile-agentic]], [[secagent-mobile-gui]]
sources:
  - url: https://hn.algolia.com/api/v1/items/47177770
    title: "Mobile-MCP: Letting LLMs autonomously discover Android app capabilities"
    date: 2026-04-16
    reliability: medium
created: 2026-04-16
updated: 2026-04-16
---

# Mobile-MCP

> 基于 Android Intent 框架的 MCP（Model Context Protocol）实现，让 LLM 助手能够自主发现设备上已安装应用的能力。

## 核心问题

当前移动 AI 助手的工具调用面临两种极端：

| 方法 | 代表 | 问题 |
|------|------|------|
| 预定义 Schema | Apple Intelligence, Google Assistant | 需要 App 主动适配助手规范，扩展性差 |
| GUI 视觉 Agent | AppAgent, AutoDroid, droidrun | 依赖截图 + 无障碍服务，能力边界模糊 |

两者的共同缺陷：**都需要预先了解具体 App 的能力**。预定义方式需要厂商协作，GUI 方式需要逆向工程。

## 方法/架构

Mobile-MCP 的核心创新是**运行时动态能力发现**，利用 Android 原生的 Intent/PackageManager 机制：

```
┌─────────────┐     PackageManager      ┌──────────────────┐
│  LLM 助手    │ ◄──────────────────── │  已安装 App       │
│  (推理引擎)  │    发现所有声明的能力    │  (MCP-style声明)  │
└──────┬──────┘                         └──────────────────┘
       │
       │ 选择 API + 生成参数
       │ (基于自然语言描述)
       ▼
┌─────────────┐     Service Binding     ┌──────────────────┐
│  能力调用    │ ─────────────────────► │  App MCP服务      │
└─────────────┘    标准Android Intent    └──────────────────┘
```

### App 侧声明（Manifest 扩展）

App 在 `AndroidManifest.xml` 中声明 MCP-style 能力，每个能力附带自然语言描述：

```xml
<service android:name=".MCPService">
  <intent-filter>
    <action android:name="ai.mcp.CAPABILITY" />
  </intent-filter>
  <meta-data
    android:name="capabilities"
    android:value='[
      {"name":"send_message","desc":"Send a text message to a contact"},
      {"name":"book_ride","desc":"Book a ride to a destination"}
    ]' />
</service>
```

### 助手侧发现流程

1. **发现阶段**：通过 `PackageManager.queryIntentServices()` 扫描所有声明了 `ai.mcp.CAPABILITY` 的服务
2. **推理阶段**：将所有发现的能力描述作为 Prompt 上下文，LLM 选择合适的工具
3. **调用阶段**：通过标准 Service Binding 或 Intent 调用选定的 API

### 与现有方案的关键区别

| 维度 | Apple/Google 方案 | GUI Agent | Mobile-MCP |
|------|-------------------|-----------|------------|
| 预定义 Schema | ✅ 必须 | ❌ | ❌ |
| 集中注册表 | ✅ 需要 | ❌ | ❌ |
| 每助手定制集成 | ✅ 必须 | ❌ | ❌ |
| 运行时动态发现 | ❌ | ❌ | ✅ |
| 能力边界清晰 | ✅ | ❌ | ✅ |
| App 无需主动适配 | ❌ | ✅ | ⚠️ 需要声明 |

## 关键洞察

1. **MCP 原生化趋势**：Hacker News 评论指出，大厂 App 未来可能直接集成 MCP，留给第三方发现层的窗口期约 12-18 个月。Mobile-MCP 的价值在于证明 Intent 框架天然适合 MCP 模式。

2. **隐私与安全的权衡**：相比 GUI Agent 的全屏读取权限，MCP 声明式能力暴露更加可控——App 只暴露它选择暴露的能力，而非整个 UI 树。

3. **生态碎片化风险**：如果每个 App 都有自己的 MCP 声明格式，助手需要处理大量异构 schema。标准化是关键——需要类似 `ai.mcp.CAPABILITY` 这样的统一 Action 名称。

4. **对移动端 Agent 的启示**：Mobile-MCP 提供了介于「完全预定义」和「完全 GUI 探索」之间的第三条路——声明式能力发现。这可能是未来端侧 Agent 工具调用的主流模式。

## 为什么重要

Mobile-MCP 解决了移动 AI Agent 最核心的工程问题：**如何让助手在不了解具体 App 的情况下安全地调用其能力**。它证明了 Android Intent 框架天然支持 MCP 模式，为端侧 Agent 提供了一种低成本、高可扩展的工具发现机制。这与 Apple Intelligence 的 App Intents 方案形成对比——后者需要严格的端到端协调，而 Mobile-MCP 允许渐进式生态演进。

## 关联
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用策略
- [[clawmobile-agentic]] — 智能手机原生 Agent 系统设计
- [[secagent-mobile-gui]] — 移动 GUI Agent 的语义上下文方案
- [[exectune-guide-core-policy]] — Agent 执行策略与 Guide Model
- [[sova-ai-android-agent]] — Sova AI：Accessibility-based 移动 Agent 的生态系统摩擦
