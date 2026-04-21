---
type: entity
tags: [android-assistant, byok, edge-ai, agent, voice-assistant, mobile]
related: [[secagent-mobile-gui]], [[gui-agent-privacy]], [[edge-cloud-offloading]], [[agent-persistent-identity]], [[mcp-deployment-patterns]]
sources:
  - url: https://aideassistant.com/
    title: "Aide — Customizable AI Assistant for Android"
    date: 2026-04-21
    reliability: medium
  - url: https://news.ycombinator.com/item?id=43824866
    title: "Show HN: Aide – A customizable Android assistant"
    date: 2026-04-21
    reliability: medium
created: 2026-04-21
updated: 2026-04-21
---

# Aide: 可定制 Android AI 助手

> BYOK 模式的 Android 助手应用，支持 Claude/ChatGPT/Ollama 等任意 OpenAI 兼容端点，替代 Google Assistant。

## 核心问题

Android 原生 Google Assistant 被锁定在单一生态内，用户无法选择模型供应商或使用本地模型。ChatGPT/Claude 官方 Android 集成无法执行设备操作（发短信、设闹钟）。Aide 填补了这个空白：**一个通用的 Android 助手壳，让用户自选 AI 大脑**。

## 架构设计

### 核心理念：瘦客户端 + 用户控制的后端
Aide 本身是一个轻量客户端，不托管任何模型或代理消息。所有推理都在用户选择的后端完成：

```
用户输入 → Aide (加密本地存储) → 直接请求用户指定的 API 端点
         ↓                                        ↓
   Android Keystore                         Claude / OpenAI / Ollama
   (AES-256 硬件加密)                      (用户的 key，用户的模型)
```

### 关键技术细节

**1. 多供应商支持**
- Claude (Anthropic)、ChatGPT (OpenAI)、Gemini (Google)
- 本地模型：Ollama、LM Studio、vLLM
- 任意 OpenAI 兼容端点（自建 API）
- 运行时切换，无需重启

**2. 安全模型**
- API 密钥存储在 Android Keystore 中，使用 AES-256 硬件级加密
- 消息直接从手机发送到用户指定的供应商，Aide 的服务器**零接触**
- 无中转服务器，无数据收集

**3. 系统集成**
- 替代 Google Assistant：角滑动、长按电源键触发
- 语音输入/输出（Pro 版）
- 设备操作：发送短信、创建日历事件、拨打电话、打开导航
- 智能家居：Home Assistant 集成

**4. Web 增强**
- 为任意模型提供实时 Web 搜索和 URL 抓取
- 即使本地 Ollama 模型也能"读取互联网"
- 解决了本地模型缺乏实时知识的痛点

### 定价模型
- **免费版**：文本对话、多供应商切换、对话历史、自定义系统提示、Web 搜索
- **Pro 版**（$9.99 一次性）：语音、照片/文件附件、设备操作、智能家居、屏幕上下文
- **无订阅**——与模型供应商的费用分离

## 实验结果/关键数据

| 维度 | Aide | Google Assistant | ChatGPT Android |
|------|------|-----------------|-----------------|
| 模型选择 | ✅ 任意模型 | ❌ 固定 | ❌ 固定 GPT |
| 本地模型 | ✅ Ollama 等 | ❌ | ❌ |
| 设备操作 | ✅ SMS/通话/闹钟 | ✅ | ❌ |
| 数据隐私 | ✅ 端到端 | ⚠️ Google 服务器 | ⚠️ OpenAI 服务器 |
| 智能家居 | ✅ Home Assistant | ✅ Google Home | ❌ |
| 价格 | $0 / $9.99 一次性 | 免费（数据付费） | $20/月 |

## 关键洞察

### 1. BYOK 模式正在成为移动端 AI 的新范式
Aide 代表了一种趋势：**AI 助手的"壳"与"大脑"分离**。用户不再需要绑定单一供应商，而是可以在不同场景使用不同模型。这与 [[edge-cloud-offloading]] 的思路一致——在端侧和云端之间动态选择。

### 2. 本地模型集成是差异化关键
Ollama/LM Studio 集成让 Aide 在隐私敏感场景（离线、无网络、敏感对话）具有独特优势。用户可以在本地运行 Gemma/Llama 处理隐私任务，同时用 Claude 处理需要深度推理的任务。

### 3. 设备操作能力决定助手实用性
纯文本 AI（如 ChatGPT Android）无法执行实际设备操作。Aide 的短信/通话/闹钟能力使其成为**真正的助手**而非仅仅是一个聊天界面。这与 [[secagent-mobile-gui]] 的 GUI Agent 研究方向互补。

## 为什么重要

对手机端 AI 生态的意义：

- **验证了端侧 AI 助手的市场需求**：用户需要可定制、隐私友好的 AI 助手
- **推动了 OpenAI 兼容端点标准**：Ollama/vLLM/LM Studio 的 OpenAI API 兼容性成为事实标准
- **挑战了 OEM 锁定**：Google Assistant 的默认地位受到第三方应用的挑战
- **为 MCP 集成提供了移动端范例**：工具调用（设备操作）+ 服务集成（Home Assistant）的模式

## 关联
- [[secagent-mobile-gui]] — GUI Agent 在移动设备上的屏幕理解能力，可与 Aide 的屏幕上下文功能互补
- [[gui-agent-privacy]] — Aide 的端到端加密模型为 GUI Agent 隐私保护提供了实践参考
- [[edge-cloud-offloading]] — Aide 支持在端侧（Ollama）和云端（Claude/GPT）之间动态切换
- [[agent-persistent-identity]] — 长期对话和个性化是 Aide 的潜在发展方向
- [[mcp-deployment-patterns]] — Aide 的设备操作能力类似于 MCP 工具调用模式
