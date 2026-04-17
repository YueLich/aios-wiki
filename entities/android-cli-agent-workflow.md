---
type: entity
tags: [android, cli, developer-tools, agent-workflow, agentic, 平台]
related: [[android-studio-agent-mode]], [[mcp-deployment-patterns]], [[sova-ai-android-agent]]
sources:
  - url: https://android-developers.googleblog.com/2026/04/build-android-apps-3x-faster-using-any-agent.html
    title: "Android CLI: Build Android apps 3x faster using any agent"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Android CLI：面向 Agent 工作流的 Android 开发命令行工具

> Google 于 2026-04-16 发布的全新 Android 开发 CLI，为 AI Agent 提供轻量级编程接口，减少 70% token 消耗，任务完成速度提升 3 倍。

## 核心问题

Android 开发者在使用 AI Agent（如 Gemini CLI、Claude Code、Codex 等）进行应用开发时，Agent 缺乏对 Android SDK 和开发环境的结构化编程接口。传统方式下，Agent 需要通过标准工具集导航复杂任务，token 消耗大、效率低。

## 工具架构

Android CLI 是一套面向 Agent 工作流的三件套：

### 1. Android CLI（命令行工具）
- **SDK 管理**：`android sdk install` 按需下载特定组件，保持开发环境精简
- **快速项目创建**：`android create` 从官方模板生成项目，确保从第一行代码就遵循推荐架构
- **设备创建与部署**：`android emulator` 创建管理虚拟设备，`android run` 部署应用
- **自动更新**：`android update` 获取最新能力

### 2. Android Skills（技能仓库）
- 基于 `SKILL.md` 的模块化指令集，提供任务的技术规范
- 设计为自动触发——当 prompt 匹配 skill 元数据时自动激活
- 首批技能包括：Navigation 3 设置迁移、Edge-to-Edge 支持、AGP 9 迁移、R8 配置分析等
- 通过 `android skills` 命令浏览安装，兼容第三方社区技能

### 3. Android Knowledge Base（知识库）
- 通过 `android docs` 命令访问，在 Android Studio 最新版中也已可用
- Agent 可搜索获取最新权威开发者指南作为上下文
- 数据源覆盖：Android 开发者文档、Firebase、Google Developers、Kotlin 文档
- 即使 LLM 训练截止日期是一年前，也能基于最新框架和模式提供指导

## 实验数据

内部实验结果：
- **Token 消耗减少 >70%**：相比 Agent 使用标准工具集
- **任务完成速度提升 3 倍**：项目和环境设置任务
- 主要效率来源：消除了 Agent 导航复杂工具链的"猜测"过程

## 设计理念

Android CLI 定位为 Agent 开发工作流的起点，而非 Android Studio 的替代品：
- 用 Agent + Android CLI 快速原型化
- 用 Android Studio 精细化 UI、调试和性能分析
- 两者的 Agent 能力互补：CLI 处理脚手架，Studio 处理深度开发

这反映了端侧 AIOS 生态的一个重要趋势：**为 Agent 提供领域专属工具接口**，而非让通用 Agent 从零理解复杂环境。

## 对手机端 AI 生态的意义

1. **Agent 工具化范式**：Android CLI 是"Agent-first developer tooling"的典型案例——工具从设计之初就为 Agent 使用优化，而非事后适配
2. **知识库 grounding**：Android Knowledge Base 解决了 LLM 知识过时问题，通过实时检索确保 Agent 始终使用最新最佳实践
3. **生态整合**：与 MCP（Model Context Protocol）理念呼应——Agent 需要标准化的方式发现和调用领域能力
4. **竞争格局**：Google 通过 Android CLI + Skills + Knowledge Base 的组合，巩固了 Android 在 AI Agent 开发领域的基础设施地位

## 关联

- [[android-studio-agent-mode]] — Android Studio 内置 Agent Mode（Panda 3），Android CLI 是其终端扩展
- [[mcp-deployment-patterns]] — MCP 部署模式与 Android Skills 的模块化 skill 设计理念一致
- [[sova-ai-android-agent]] — SOVA AI Android Agent，同属 Android 平台上的 Agent 生态
- [[clawmobile-agentic]] — 手机原生 Agent 系统，Android CLI 为其提供开发工具链
- [[mobile-mcp]] — Mobile MCP 让 LLM 自主发现 Android 应用能力
