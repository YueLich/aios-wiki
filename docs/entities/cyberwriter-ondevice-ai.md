---
type: entity
tags: [工具应用, macOS, Apple Intelligence, 端侧AI, Foundation Models, 编辑器]
related: [[apple-coreml-9]], [[gemma4-ondevice]], [[edge-llm-apple-intelligence]]
sources:
  - url: https://cyberwriter.app
    title: "cyberWriter - Native Markdown Editor for macOS"
    date: 2026-04-20
    reliability: medium
  - url: https://news.ycombinator.com/item?id=43805000
    title: "Show HN: CyberWriter – a .md editor built on Apple's on-device AI"
    date: 2026-04-20
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# CyberWriter: 基于 Apple 端侧 AI 的原生 Markdown 编辑器

> macOS 原生 Markdown 编辑器，集成 Apple Foundation Models（macOS 26+）实现零配置端侧 AI 写作辅助

## 核心价值

CyberWriter 是首批深度集成 Apple macOS 26 Foundation Models API 的生产力应用之一。Apple 在 macOS 26 中悄然内置了一个约 30 亿参数的端侧 LLM，支持流式输出、结构化生成和工具调用，但几乎没有开发者在使用这些 API。CyberWriter 证明了这套端侧 AI 栈的实际可用性。

## 技术架构

### Apple Foundation Models 集成
- **模型规模**: ~3B 参数的端侧 LLM，随 macOS 26 预装
- **API 特性**: 流式输出（streaming）、结构化输出（structured output）、工具调用（tool use）
- **零配置**: 无需 API key、无需云端调用、无需下载模型——macOS 26+ 开箱即用
- **隐私**: 所有推理完全在设备上进行

### AI 工作区功能
- **Stream-to-editor**: AI 响应直接实时输入到光标位置
- **上下文操作**: 选中文本后执行摘要、改写、解释、语气转换
- **多模型支持**: Apple Intelligence（端侧）+ OpenRouter（云端免费/付费模型）+ Claude（Anthropic 原生 API）+ 本地 LLM
- **统一撤销**: AI 插入的内容作为单一撤销组处理

### 编辑器特性
- 完整 Markdown 扩展支持 + 内联 CSS/HTML
- KaTeX 数学公式原生渲染
- 16 种 Mermaid 图表类型
- 语音笔记 + 端侧语音转写（on-device speech recognition）
- 幻灯片/闪卡生成 + 间隔重复学习
- 15+ 语法主题
- 纯 SwiftUI 原生实现，零 Electron 依赖

## 为什么重要

1. **Apple 端侧 AI 落地案例**: CyberWriter 是少数真正用上 macOS 26 Foundation Models API 的应用，展示了端侧 ~3B 参数模型在实际生产力场景中的能力边界
2. **隐私优先的 AI 辅助写作**: 完全端侧推理意味着用户的文档内容永远不离开设备
3. **端侧模型的实用性验证**: 如果 3B 参数的模型能胜任 Markdown 写作辅助，这对端侧 AI 部署的可行性是有力证据
4. **开发者启示**: Apple 端侧 AI API 被严重低估——super easy API + no one wiring them together yet

## 关联

- [[apple-coreml-9]] — CoreML 工具链支撑端侧模型部署
- [[gemma4-ondevice]] — 另一端侧模型选项，对比 Apple 自研 Foundation Models
- [[edge-llm-apple-intelligence]] — Apple 端侧 LLM 生态的整体布局
- [[on-device-streaming-asr]] — 端侧语音转写技术，CyberWriter 的语音笔记功能依赖此技术
- [[mnn-350]] — 阿里 MNN 推理框架，对比 Apple 原生方案
