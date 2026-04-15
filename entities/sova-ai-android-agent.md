---
type: entity
tags: [android, accessibility-api, ai-agent, app-automation, no-root, 智能体, 应用操控]
related: [[clawmobile-agentic]], [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[mga-memory-gui-agent]], [[android-studio-agent-mode]]
sources:
  - url: https://news.ycombinator.com/item?id=47738583
    title: "Show HN: Android AI agent-assistant operating your apps"
    date: 2026-04-14
    reliability: medium
  - url: https://ayconic.io/sova
    title: "Sova AI - Android Agent"
    date: 2026-04-14
    reliability: medium
created: 2026-04-15
updated: 2026-04-15
---

# Sova AI — Android 原生应用操控 Agent

> 真正操控手机 App 的 Android Agent——点击、滚动、打字——无需 root、adb、PC，仅通过 Accessibility API 实现。由 Ayconic 团队开发，2026 年 4 月在 HN 发布。

## 核心问题

当前 Android 上的 AI 助手（如 Gemini）虽然深度集成在 OS 中，但如果你说"叫个 Uber 去机场"，它们大多只返回搜索结果或打开 App 按钮，**不做实际工作**。Sova 要解决的是：让 AI Agent 真正像人一样操作手机。

## 方法/架构

### 操控机制：Accessibility API

Sova 不依赖不存在的官方 App API，而是**模拟人类操作**：
- 使用 Android Accessibility API 读取屏幕的 UI 节点树（UI node tree）
- 像虚拟人一样执行：点击、滚动、打字
- **不需要**：root、adb、PC、Appium、USB、Shizuku、浏览器

这是一个标准 Kotlin App，任何用户都能直接安装使用。

### AI 模型支持

- 当前支持主流云端 AI 提供商：OpenAI、Gemini、Anthropic、DeepSeek 等
- 正在开发本地 AI 模型支持：Ollama、LM Studio 等
- **100% 免费 / BYOK（Bring Your Own Key）模式**：用户自备 API Key，Sova 引擎本身免费

### 交互方式

- 语音或文本输入 prompt
- 可设为默认助手
- 自主决策执行路径，无需用户逐步指导

## 实验结果/关键数据

**Demo 示例**：语音下单汉堡——Agent 自动操作手机完成整个流程，无需人工干预（[视频演示](https://www.youtube.com/shorts/WzvOsbhOz1k)）。

**与竞品对比**：
| 方案 | 需 root/adb | 需 PC | 实际操控 | 价格 |
|------|-----------|-------|---------|------|
| Sova AI | ❌ | ❌ | ✅ 真实操作 | 免费/BYOK |
| Gemini 助手 | ❌ | ❌ | ❌ 仅搜索/打开 | 内置 |
| Perplexity 助手 | ❌ | ❌ | ❌ 仅浏览器 Agent | 付费 |
| Appium/ADB 方案 | ✅ | ✅ | ✅ | 开发者专用 |

## 关键洞察

### Google Play 审核困境

Sova 因使用 Accessibility API 进行"通用自动化"（映射并点击其他 App）而被 Google Play 拒绝。这是 Android 生态的核心矛盾：
- Google 鼓励构建"agentic behavior"（Gemini 的承诺）
- 但 Accessibility API 的"滥用"政策禁止真正实现 agentic 操控
- 这迫使开发者转向 F-Droid、Aurora 等替代分发渠道

### Accessibility API 是 Mobile Agent 的事实标准

无论是 Sova、ClawMobile 还是其他方案，**Accessibility API 是当前唯一可行的跨 App 操控接口**。这既是优势（跨平台、无需 root），也是瓶颈（受限于 Google 审核政策）。

### 从"助手"到"Agent"的跨越

Sova 代表了从"AI 助手"（给你信息）到"AI Agent"（替你做事）的关键转变。真正的 Agent 需要：
1. 理解屏幕状态（通过 Accessibility 读取 UI tree）
2. 决策执行路径（LLM 推理）
3. 执行精确操作（模拟人类输入）
4. 处理异常和失败（自修复）

## 为什么重要

Sova 验证了一个关键假设：**在不需要 root 和特殊权限的情况下，通过 Accessibility API + LLM 就能实现真正的手机操控 Agent**。这对手机端 AIOS 意味着：
- Agent 框架不需要 OS 级深度集成也能工作
- BYOK 模式降低了用户门槛
- Google Play 的审核限制可能推动 Agent 功能走向侧载生态

## 关联

- [[clawmobile-agentic]] — 同样的 Accessibility API 操控思路，但在框架层面重新设计
- [[secagent-mobile-gui]] — 移动 GUI Agent 的语义上下文处理
- [[pspa-bench-gui-agent]] — 智能手机 GUI Agent 的个性化基准
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent，可补充 Sova 的对话连续性
- [[android-studio-agent-mode]] — Android Studio 的 Agent 模式开发体验
