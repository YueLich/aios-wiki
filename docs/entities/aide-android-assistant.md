---
type: entity
tags: [Android assistant, 移动Agent, 语音助手, 端侧AI, 个人助理, LLM integration, BYOK]
related: [[google-assistant-gemini-transition]], [[secagent-mobile-gui]], [[visionclaw-wearable-agent]], [[on-device-vs-cloud-agentic-tool-calling]], [[android-hybrid-inference]]
sources:
  - url: https://aideassistant.com/
    title: "Aide: A Customizable Android Assistant"
    date: 2026-04-21
    reliability: medium
  - url: https://hn.algolia.com/api/v1/items/47848512
    title: "Show HN: Aide – A customizable Android assistant"
    date: 2026-04-21
    reliability: medium
created: 2026-04-21
updated: 2026-04-21
---

# Aide: 可定制 Android 语音助手

> 开源 Android 助手应用，可注册为系统默认数字助手，支持自带 API Key 接入 Claude/OpenAI/Ollama/LM Studio——实现了"Google Assistant 替代品"的用户需求。

## 核心功能

Aide 是一个 Android 应用，可以注册为系统的默认数字助手（default assistant），替换 Google Assistant：

- **触发方式：** 角落滑动（corner-swipe）和电源键长按（power-button-hold）
- **多 Provider 支持：** Claude、OpenAI、或任何 OpenAI 兼容端点（Ollama、LM Studio、vLLM）
- **隐私设计：** API Key 在设备端加密存储，对话直接发送到用户选择的 provider
- **Bring Your Own Key (BYOK)：** 不依赖任何中间服务器，用户直接用自己的 API Key

## 技术架构

### 系统集成

作为 Android 默认助手，Aide 利用 Android 的 `VoiceInteractionService` API：
- 系统级调用入口（非应用内启动）
- 语音输入 + 文本交互
- 替代 Google Assistant 的完整调用链

### Provider 抽象

```
用户 → Aide (Android) → 加密 API Key → 用户选择的 LLM Provider
                            ├── Claude API
                            ├── OpenAI API
                            ├── Ollama (本地)
                            ├── LM Studio (本地)
                            └── vLLM (本地)
```

支持本地模型（Ollama/LM Studio/vLLM）意味着可以实现完全端到端的隐私保护——语音输入→本地模型推理→响应，全程无数据离开设备。

## 关键洞察

1. **BYOK 模式趋势：** Aide 代表了一类新兴的"用户掌控 AI"应用——不依赖厂商锁定，用户自行选择模型和 provider
2. **本地模型支持是关键差异化：** 支持 Ollama/LM Studio 意味着隐私敏感用户可以完全本地运行，这在 Google Assistant 或 ChatGPT App 中无法实现
3. **系统级集成的重要性：** 能注册为 Android 默认助手是核心竞争力——不是另一个 app，而是替代系统组件
4. **开发者信息：** 作者自述"想要 Google 之外的选择，但 ChatGPT 和 Claude 应用的集成无法在设备上做任何事"——这反映了当前 AI 助手生态的碎片化痛点

## 当前状态

- **阶段：** 早期（Show HN，1 point）
- **开源：** 是
- **限制：** 依赖 API 调用（即使是本地模型也需要本地推理服务器运行）

## 为什么重要

对手机端 AI 生态的意义：
- **Android 助手生态碎片化：** Google Assistant 向 Gemini 过渡期间，用户需要替代品。Aide 填补了这个空白
- **端云混合灵活度：** 用户可以按需选择云端大模型或本地小模型，甚至在同一应用中切换
- **隐私优先设计：** BYOK + 本地模型支持 = 无中间服务器 = 对隐私敏感用户友好
- **Agent 系统参考实现：** 作为 Android 默认助手的开源实现，为移动 Agent 开发提供参考架构

## 关联

- [[google-assistant-gemini-transition]] — Google Assistant → Gemini 过渡背景
- [[secagent-mobile-gui]] — 高效移动 GUI Agent
- [[visionclaw-wearable-agent]] — 始终在线的可穿戴 AI Agent
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端 Agent 工具调用对比
- [[android-hybrid-inference]] — Android 端云协同 API
- [[agentopt-client-side-optimization]] — 客户端 Agent 优化框架
