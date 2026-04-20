---
type: entity
tags: [on-device, mobile-ai, offline, gguf, llama-cpp, stable-diffusion, whisper, privacy, tool-calling, React Native, edge-ai]
related: [[ggml-llamacpp-hf]], [[mnn-350]], [[gemma4-ondevice]], [[on-device-vs-cloud-agentic-tool-calling]], [[sustainability-ondevice-intelligence]], [[mobile-aios-overview]]
sources:
  - url: https://github.com/alichherawalla/off-grid-mobile-ai
    title: "Off Grid - GitHub Repository"
    date: 2026-04-20
    reliability: high
  - url: https://play.google.com/store/apps/details?id=ai.offgridmobile
    title: "Off Grid - Google Play"
    date: 2026-04-20
    reliability: high
  - url: https://apps.apple.com/us/app/off-grid-local-ai/id6759299882
    title: "Off Grid - App Store"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Off Grid — 端侧全功能 AI 套件

> **一句话概括**：一个集成了文本生成、图像生成、视觉理解、语音转写、工具调用的端侧离线 AI 应用，支持 Android/iOS/macOS，1623 GitHub Stars。
> **来源**：GitHub (alichherawalla/off-grid-mobile-ai), 最新版本 v0.0.89 (2026-04-17)

## 核心问题

大多数"本地 LLM"应用只提供聊天功能。Off Grid 的愿景是构建一个完整的端侧 AI 工作站——在手机上完成所有 AI 任务，数据永不离开设备。这解决了：
1. **隐私敏感场景**：企业文档分析、医疗记录处理等场景需要数据本地化
2. **离线可用性**：野外作业、飞机上、网络不稳定地区的 AI 需求
3. **多模态整合**：将文本、视觉、语音、图像生成统一在一个端侧应用中

## 方法/架构

### 技术栈
- **框架**：React Native (TypeScript) + 原生模块 (Java/Swift)
- **LLM 推理**：基于 llama.cpp 的 GGUF 模型运行，支持 Qwen 3、Llama 3.2、Gemma 3、Phi-4 等
- **图像生成**：端侧 Stable Diffusion，NPU 加速 (骁龙) / Core ML (iOS)，支持 20+ 模型
- **视觉理解**：SmolVLM、Qwen3-VL、Gemma 3n
- **语音**：端侧 Whisper 语音转文字
- **知识库**：端侧 MiniLM 嵌入 + SQLite 向量检索 + 余弦相似度

### 核心功能模块

| 模块 | 实现 | 性能 |
|------|------|------|
| 文本生成 | GGUF 模型, streaming | 旗舰机 15-30 tok/s, 中端 5-15 tok/s |
| 图像生成 | Stable Diffusion NPU/CoreML | NPU 5-10s, CPU 15-30s |
| 视觉理解 | SmolVLM/Qwen3-VL | 旗舰机 ~7s |
| 语音转写 | Whisper 端侧 | 实时 |
| 工具调用 | 内置工具链 (搜索/计算器/知识库) | 自动 tool loop |
| 远程 LLM | OpenAI 兼容服务器发现 (Ollama/LM Studio) | SSE 流式 |

### 架构特点
- **端侧 RAG**：PDF/文档通过 MiniLM 在端侧嵌入，存储在本地 SQLite，无需云端向量数据库
- **工具调用安全**：内置 runaway prevention 机制，防止模型无限调用工具循环
- **混合推理**：支持本地 GGUF 模型和局域网远程 LLM 无缝切换
- **NPU 加速**：骁龙平台使用 NPU 进行 Stable Diffusion 推理，将图像生成从 30s 压缩到 5-10s

## 实验结果/关键数据

### 性能基准 (2026-04)

| 任务 | 旗舰设备 | 中端设备 | 测试硬件 |
|------|----------|----------|----------|
| 文本生成 | 15-30 tok/s | 5-15 tok/s | 骁龙 8 Gen 2/3, A17 Pro |
| 图像生成 (NPU) | 5-10s | — | 骁龙 8 Gen 3 |
| 图像生成 (CPU) | ~15s | ~30s | 通用 |
| 视觉推理 | ~7s | ~15s | 旗舰设备 |
| 语音转写 | 实时 | 实时 | 全平台 |

### 生态规模
- GitHub Stars: 1,623 (2026-04-20)
- 版本: v0.0.89 (2026-04-17)
- 支持平台: Android, iOS (App Store), macOS (Mac Catalyst)
- 支持模型格式: GGUF (任意量化模型)
- Topics: edge-ai, gguf, llama-cpp, local-ai, mobile-ai, offline-ai, ondevice, privacy-first

## 关键洞察

1. **全功能集成是端侧 AI 应用的趋势**：Off Grid 证明了将 LLM、视觉、语音、图像生成、RAG 统一到单一离线应用是可行的。这比每次开发单一功能的端侧应用更高效。

2. **NPU 加速的商业价值**：骁龙 NPU 将 Stable Diffusion 生成时间从 15-30s 降低到 5-10s，这使得端侧图像生成从"技术 demo"变为"可用功能"。这为更多 NPU 驱动的端侧 AI 应用铺平道路。

3. **端侧 RAG 的可行性**：通过 MiniLM 嵌入 + SQLite 余弦相似度，Off Grid 在手机上实现了文档级 RAG。这证明复杂的检索增强生成可以完全端侧化，无需向量数据库服务。

4. **Tool Calling 安全机制**：内置 runaway prevention 是一个值得借鉴的设计。端侧 tool calling 没有云端的成本约束（token 限制），更容易出现无限循环，必须有硬性限制。

5. **混合本地/远程推理**：自动发现局域网内 Ollama/LM Studio 服务器并无缝切换，这是端侧 AI 应用的实用创新——在手机算力不足时，自动委派到局域网高性能机器。

## 为什么重要

Off Grid 是目前**功能最完整的端侧离线 AI 应用**之一（1623 Stars），代表了 Mobile AIOS 生态中"应用层"的成熟方向：

1. **隐私优先**：完整实现了数据零外传的端侧 AI 工作流，验证了隐私计算在消费级应用中的可行性
2. **多模态整合**：将 LLM + 视觉 + 语音 + 图像生成统一到一个端侧应用，这是 Mobile AIOS 的核心愿景
3. **模型生态兼容**：支持任意 GGUF 模型，不绑定特定模型厂商，促进端侧模型生态多样性
4. **硬件加速落地**：骁龙 NPU 的 Stable Diffusion 加速是 NPU 在消费级应用中的成功案例

## 关联

- [[ggml-llamacpp-hf]] — Off Grid 的核心推理引擎，基于 llama.cpp 的 GGUF 模型运行
- [[mnn-350]] — 另一端侧推理框架，对比 Off Grid 的纯 llama.cpp 路线
- [[gemma4-ondevice]] — Off Grid 支持的端侧模型之一
- [[on-device-vs-cloud-agentic-tool-calling]] — Off Grid 的 tool calling 实现提供了端侧 vs 云端调用的实际案例
- [[sustainability-ondevice-intelligence]] — Off Grid 的离线模式展示了端侧 AI 的能效优势
- [[mobile-aios-overview]] — Off Grid 是 Mobile AIOS 应用层的典型代表
