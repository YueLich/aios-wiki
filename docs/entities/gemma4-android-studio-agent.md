---
type: entity
tags: [gemma4, android-studio, agent-mode, on-device, local-inference, coding-assistant, google]
related: [[gemma4-ondevice]], [[android-studio-agent-mode]], [[on-device-vs-cloud-agentic-tool-calling]]
sources:
  - url: https://android-developers.googleblog.com/2026/04/android-studio-supports-gemma-4-local.html
    title: "Android Studio supports Gemma 4: our most capable local model for agentic coding"
    date: 2026-04-02
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Gemma 4 Android Studio Agent Mode

> Google 将 Gemma 4 集成到 Android Studio 的 Agent Mode，支持完全本地运行的 AI 编码助手。

## 核心问题

开发者需要 AI 编码辅助，但云端方案存在隐私泄露风险、API 配额限制和网络依赖问题。在企业安全环境或离线场景下，云端 Agent 无法使用。Google 的解决方案是将 Gemma 4 直接运行在开发者本机上，通过 Android Studio 的 Agent Mode 提供完整的本地化 AI 编程体验。

## 架构与能力

### 模型变体与硬件需求

| 模型 | 总 RAM 需求 | 存储需求 | 适用场景 |
|------|------------|---------|---------|
| Gemma E2B | 8 GB | 2 GB | 轻量级代码补全 |
| Gemma E4B | 12 GB | 4 GB | 中等复杂度任务 |
| Gemma 26B MoE | 24 GB | 17 GB | 复杂 Agent 工作流 |

26B MoE（Mixture of Experts）是推荐的默认选择，在保持高质量推理的同时，通过稀疏激活降低实际计算开销。

### Agent Mode 核心功能

1. **功能设计与生成**：开发者输入 "build a calculator app"，Agent 自动生成完整 UI 代码，遵循 Kotlin + Jetpack Compose 最佳实践
2. **大规模重构**：高阶指令如 "Extract all hardcoded strings and migrate to strings.xml"，Agent 扫描整个代码库并跨文件批量修改
3. **Bug 修复与构建解析**：输入 "Build my project and fix any errors"，Agent 定位错误代码并迭代修复直到构建成功
4. **离线可用**：无需网络连接即可完成所有 Agent 操作
5. **隐私安全**：所有处理在本机完成，代码不离开设备

### 技术实现

- 通过 LM Studio 或 Ollama 作为本地 LLM Provider
- Android Studio Settings > Tools > AI > Model Providers 配置
- Gemma 4 专门针对 Android 开发训练，具备 agentic tool-calling 能力
- 利用本地 GPU 和 RAM 进行推理优化

## 关键洞察

### 端侧 Agent 的里程碑

这是 Google 首次将一个完整的 Agent 工作流（不只是代码补全）部署到开发者本机。与简单的 inline suggestions 不同，Agent Mode 需要：
- **多步推理**：理解复杂指令，规划执行步骤
- **工具调用**：读写文件、执行构建命令、修改多文件
- **错误恢复**：构建失败后自动诊断并迭代修复

Gemma 4 的 26B MoE 架构使其在 24GB RAM 的消费级硬件上就能运行这种复杂工作流，这对端侧 Agent 意义重大。

### 对移动 AI 生态的影响

1. **验证了端侧 Agent 的可行性**：如果 Gemma 4 能在笔记本上运行完整 Agent 工作流，那么在手机上运行轻量级 Agent 只是时间问题
2. **MoE 架构的优势**：26B MoE 可能只激活部分参数，实际推理开销远低于 26B dense 模型
3. **隐私驱动的端侧化趋势**：从 Gemini Nano（手机端）到 Gemma 4（开发机端），Google 正在构建完整的端侧 AI 生态

## 关联

- [[gemma4-ondevice]] — Gemma 4 的端侧部署全景
- [[android-studio-agent-mode]] — Android Studio Agent Mode 早期集成
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用的权衡
- [[minicpm-242]] — MiniCPM 作为端侧 Agent 的竞品
