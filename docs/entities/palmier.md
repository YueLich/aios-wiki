---
type: entity
tags: [agent, tool-calling, mobile-bridge, phone-integration, on-device]
related: [[mcp-deployment-patterns]], [[agent-persistent-identity]], [[on-device-vs-cloud-agentic-tool-calling]]
sources:
  - url: https://github.com/caihongxu/palmier
    title: "Palmier - GitHub"
    date: 2026-04-21
    reliability: high
  - url: https://www.palmier.me
    title: "Palmier 官网"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Palmier: AI Agent 与手机的双向桥梁

> 一个开源工具，让桌面端的 AI Agent 能与手机双向通信——调度任务、推送通知、读取 SMS/日历/联系人

## 核心问题

当前 AI Agent（如 Claude Code、Gemini CLI、Codex CLI）运行在桌面环境中，无法感知用户的手机状态（短信、通知、日历事件），也无法向手机推送结果。用户需要在终端前才能与 Agent 交互，限制了 Agent 的实际效用。

## 架构与工作原理

Palmier 由三部分组成：

1. **后台守护进程**：运行在用户桌面机器上（systemd/launchd/Task Scheduler），负责调用 Agent CLI
2. **MCP Server**：暴露标准 MCP 接口，Agent 可通过 MCP 协议访问手机能力
3. **PWA 应用**：移动端友好界面，通过 HTTP 或 relay server 连接到守护进程

**核心能力**：
- 📱 **手机 → Agent**：从手机调度一次性任务、定时执行周期任务、审批权限请求、查看执行结果
- 🖥️ **Agent → 手机**：推送通知和全屏闹钟、发送问题给用户、读取 SMS/通知、管理联系人和日历
- 🔗 **MCP 集成**：作为 MCP Server 暴露手机能力给任何支持 MCP 的 Agent

**支持的 Agent**：Claude Code、Gemini CLI、Codex CLI、GitHub Copilot、OpenClaw 等 15+ Agent CLI

**跨平台**：Linux (systemd)、macOS 13+ (launchd)、Windows 10/11 (Task Scheduler)

**安装方式**：
```bash
# Linux / macOS
curl -fsSL https://palmier.me/install.sh | bash
# 或 npm
npm install -g palmier
```

## 为什么重要

Palmier 解决了 Agent 生态中的一个关键空白——**Agent 缺乏对物理世界的感知**。通过桥接手机，Agent 可以：

1. **感知真实世界事件**：日历提醒、SMS 验证码、位置信息
2. **异步交互**：用户离开终端后，Agent 仍可通过手机联系用户
3. **离线能力**：Agent 运行在本地桌面，不依赖云端 API
4. **MCP 标准化**：作为 MCP Server，与现有 MCP 生态无缝集成

这直接指向手机端 AIOS 的核心需求——**设备与 Agent 之间的深度集成**。Palmier 提供了一种轻量级、开源的实现路径。

## 关联

- [[mcp-deployment-patterns]] — MCP Server 部署模式的实践案例
- [[agent-persistent-identity]] — Agent 需要跨设备持久化身份
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用的取舍
- [[secagent-mobile-gui]] — 手机 GUI Agent 的另一种路径
