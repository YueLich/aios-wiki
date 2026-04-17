---
type: entity
tags: [gemini-nano, google, chrome, browser, on-device, llm, prompt-api, web]
related: [[gemma4-ondevice]], [[gemma-cpp-inference]], [[react-native-llm-edge]], [[google-ai-edge-gallery]]
sources:
  - url: https://www.swyx.io/gemini-nano
    title: "Gemini Nano in Chrome 137: notes for AI Engineers"
    date: 2025-07-08
    reliability: medium
  - url: https://developer.chrome.com/docs/ai/prompt-api
    title: "Chrome Prompt API documentation"
    date: 2025-07-08
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Gemini Nano Chrome 137：浏览器端内置 LLM

> Chrome 137 开始逐步向所有用户推送 Gemini Nano——一个内置于浏览器的端侧 LLM。模型大小约 1.5-2.4GB（推断为 4-6B 参数量级，4-8bit 量化），支持 6K token 上下文。通过 Prompt API 为 Web 开发者提供本地 AI 能力。

## 核心概况

Google 的端侧模型 Gemini Nano 正在从 Chrome 137 开始逐步部署到所有 Chrome 用户。这是**浏览器级别的端侧 AI 推理**——无需服务器、无需 API key、所有推理在用户设备上完成。

### 技术规格

| 参数 | 值 |
|------|-----|
| Chrome 版本 | 137+ |
| 模型大小 | ~1.5-2.4GB（下载） |
| 推断参数量 | 4-6B（推断，4-8bit 量化） |
| 上下文窗口 | 6K tokens |
| 启用方式 | chrome://flags/#prompt-api-for-gemini-nano |
| 多模态 | 支持音频和图像输入（可选） |

## API 使用

### 基本设置

```javascript
const session = await LanguageModel.create({
  monitor(m) {
    m.addEventListener("downloadprogress", (e) => {
      console.log(`Downloaded ${e.loaded * 100}%`);
    });
  },
  // 可选：启用多模态输入
  // expectedInputs: [{ type: "audio" }, { type: "image" }]
});
```

### 上下文容量

```javascript
session.inputQuota // 6144 tokens
```

### 结构化输出（JSON Schema）

通过 initialPrompts 注入 schema 示例来引导模型输出结构化 JSON。这与 function calling 的模式一致，但需要 few-shot 示例来稳定格式。

## 对手机端 AI 生态的意义

1. **浏览器即 AI 运行时**：Web 开发者可以在不依赖后端的情况下构建 AI 功能，降低端侧 AI 的门槛
2. **隐私优先**：所有推理在用户设备上完成，数据不离开浏览器
3. **模型量级启示**：4-6B 量化模型 + 6K 上下文是当前端侧浏览器推理的可行配置
4. **与 Gemma 4 E2B/E4B 互补**：Gemini Nano 是 Chrome 内置的闭源方案，Gemma 4 E2B 是开源替代，两者针对相似的端侧场景
5. **Prompt API 模式**：Chrome 的 Prompt API 可能成为浏览器端 AI 的事实标准

## 注意事项

- 当前仍需在 chrome://flags 中手动启用（Chrome 137+ 开始逐步 unflag）
- 与早期 window.ai 的过度承诺不同，当前实现更务实但 API 设计不够"干净"
- 6K token 上下文限制了复杂任务
- swyx 的原始文章来自 2025-07-08，Chrome 137+ 已开始逐步推送

## 关联

- [[gemma4-ondevice]] — Gemma 4 E2B 是 Chrome 内置 Nano 的开源替代方案
- [[gemma-cpp-inference]] — llama.cpp 可用于运行 Gemma 系列模型
- [[react-native-llm-edge]] — React Native 端侧 LLM 部署方案
- [[google-ai-edge-gallery]] — Google AI Edge Gallery 提供更多端侧 AI 示例
