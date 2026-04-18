---
type: concept
tags: [Android, CLI, Agent, 开发工具, 自动化, Google]
related: [[gemma4-aicore]], [[gemini-31-flash-lite]], [[clawmobile-agentic]], [[android-agent-assistant]]
sources:
  - url: https://android-developers.googleblog.com/2026/04/build-android-apps-3x-faster-using-any-agent.html
    title: "Android CLI and skills: Build Android apps 3x faster using any agent"
    date: 2026-04-16
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# Android CLI: Agent 驱动的 Android 开发工具

> Google 推出的 Android CLI 及 Android Skills 体系，为 Agent 提供程序化接口进行 Android 应用开发，内部实验显示 Agent 完成任务速度提升 3 倍，token 使用量减少 70%。

## 核心问题
Agent 辅助 Android 开发面临效率瓶颈：Agent 需要通过阅读文档、猜测 API 用法来完成任务，这导致大量 token 浪费和频繁的试错。传统的描述性文档对人类学习友好，但对 LLM Agent 不够精确。

## 架构设计

### Android CLI
一个轻量级命令行工具，提供程序化接口：
- `create`：秒级创建 Android 项目
- `run`：在模拟器/设备上运行应用
- `test`：执行测试
- `ui`：Agent 导航 UI

### Android Skills
面向 Agent 的技能系统：
- **精确、可执行的指令**（而非概念性文档）
- **覆盖完整工作流**：从项目创建到 UI 测试
- **减少 LLM 幻觉**：Agent 通过 Skills 执行而非猜测

### Android Knowledge Base
结构化的 Android 开发知识库：
- 专为 LLM 优化的文档格式
- 减少 Agent 需要搜索的信息量

## 实验数据

| 指标 | 无 Android CLI | 使用 Android CLI | 提升 |
|------|--------------|-----------------|------|
| Token 使用量 | 基线 | 减少 70%+ | ⬇️ 70% |
| 任务完成时间 | 基线 | 快 3x | ⬆️ 300% |
| 幻觉/错误率 | 高 | 显著降低 | ⬇️ 大幅 |

## 关键洞察

1. **Agent 工具化的范式转变**：传统开发工具为人类设计（GUI、文档）。Android CLI 是第一个专为 Agent 设计的 Android 开发工具——通过 CLI 命令而非 GUI 交互。这代表了"Agent-first"工具设计的开始。

2. **Skills 作为 Agent 的"程序性知识"**：人类开发者通过经验积累"怎么做"的知识（如如何设置 Gradle 依赖）。Skills 将这种程序性知识编码为 Agent 可执行的格式，避免 Agent 每次都从零推理。

3. **对端侧 Agent 的启示**：如果 Agent 能高效开发 Android 应用，端侧 Agent 也可能通过类似的 Skills 系统操作手机上的应用——参考 [[clawmobile-agentic]] 的原生 Agent 架构。

4. **与 AICore/Gemma 4 的协同**：Android CLI + Gemma 4 + AICore = 从开发到部署的完整 Agent 生态。开发者可以用 Agent 开发应用，应用内部也可以使用 Gemma 4 驱动 Agent 功能。

## 为什么重要

- **Agent 辅助开发的里程碑**：从"Agent 读文档猜 API"到"Agent 通过 CLI 精确执行"
- **为 Android Agent 生态铺路**：CLI/Skills 模式可推广到端侧 Agent 操作应用
- **Token 效率革命**：70% token 减少意味着 Agent 开发成本大幅降低
- **多 Agent 系统的基础设施**：Android CLI 可作为多 Agent 协作的统一接口

## 关联
- [[gemma4-aicore]] — Gemma 4 是 Android Agent 的端侧推理引擎
- [[clawmobile-agentic]] — 原生 Android Agent 架构，可利用 Android CLI
- [[gemini-31-flash-lite]] — Agent 辅助开发中的云端路由选择
- [[android-agent-assistant]] — 基于 Accessibility API 的 Android Agent
