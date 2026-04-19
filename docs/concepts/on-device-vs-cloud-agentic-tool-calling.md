---
type: concept
tags: [on-device, agentic, tool-calling, ios, apple, inference, comparison]
related: [[orion-apple-neural-engine-llm]], [[gemma4-ondevice]], [[edge-cloud-offloading]], [[huoziime-ondevice-ime]]
sources:
  - url: https://subralabs.com/lab/on-device-vs-cloud-llm.html
    title: "On-Device vs Cloud LLMs for Agentic Tool Calling"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# On-Device vs Cloud LLMs for Agentic Tool Calling

> SubraLabs 在真实 iOS 应用中对比 Apple 端侧 3B 模型与 GPT-20B 云端模型的 Agentic 工具调用能力——结论是 3B 模型在复合任务上全面失败。

## 核心问题

端侧 LLM 能否胜任多步工具编排（reason → act → synthesise 循环）？这是决定移动端 Agent 能力边界的关键问题。

## 实验设置

- **应用场景**: iOS 度假村目录 App 的对话式旅行顾问
- **端侧**: Apple Foundation Models（iOS 26, ~3B 参数），通过 Swift @Generable 宏实现结构化生成和工具调用
- **云端**: GPT-OSS 20B via OpenRouter，SSE 流式传输
- **三个工具**: searchHotels（自由文本搜索）、applyFilters（结构化过滤）、searchHotelsNearAirport（哈弗赛因距离计算）
- **数据集**: ~85 个度假村属性

## 关键发现

### 发现 1: 工具调用复杂度是瓶颈

3B 模型能正确识别工具并生成参数，但**复合任务失败率极高**：

| 失败模式 | 示例 |
|---------|------|
| 计数错误 | 返回 2 个结果却说"找到 3 个匹配" |
| 自相矛盾 | "没找到匹配"→ 紧接着列出正确的 2 个结果 |
| 上下文丢失 | "其中哪些有泳池？"触发全新搜索而非过滤上一轮结果 |

Chain-of-thought、分离决策/响应阶段、few-shot 等提示工程方法均无法可靠解决。**这不是提示工程问题，是参数量问题。**

### 发现 2: 响应质量差距

- 云端模型维持一致的"资深旅行顾问"人设，理解隐含意图（"放松的地方"→ spa 评分+环境评分）
- 端侧模型产出语法正确但缺乏语境的意大利语，更像数据库打印而非推荐

### 发现 3: 成本不是障碍

| 指标 | 数值 |
|------|------|
| 每 100K tokens 成本 | $0.005-$0.007 |
| 每次对话（5 轮） | ~8K-12K tokens |
| 每次对话成本 | ~$0.001 |
| 月 1000 次对话 | ~$0.50-$0.70 |

成本低到可以完全吸收或包含在免费增值模型中。

### 综合对比矩阵

| 维度 | 端侧 (~3B) | 云端 (20B) |
|------|-----------|-----------|
| 简单工具调用 | ✅ 可用 | ✅ 可用 |
| 复合 Agentic 任务 | ❌ 不可靠 | ✅ 可靠 |
| 响应连贯性 | 功能性 | 自然 |
| 非英语质量 | 可接受 | 强 |
| 隐私 | 完全 | 需信任提供方 |
| 延迟 | 即时首 token | 可接受（流式） |
| 离线能力 | 完全 | 无 |
| 每次对话成本 | $0 | $0.001 |

## 决策框架

- **用端侧**: 单步任务（分类、提取、摘要、单工具调用+简单响应）
- **用云端**: 需要多步推理、工具编排、人设一致性或强非英语生成
- **提供切换**: 当用户群体包含隐私优先用户，或需要离线降级时

## 关键洞察

这项研究揭示了端侧 AI 的一个根本性边界：**工具调用的机械能力 ≠ 工具结果的理解能力**。3B 模型知道*如何调用*工具，但不知道*如何解释*返回的数据——计数、矛盾检测、上下文保持都失败了。这意味着端侧 Agent 目前只能做"执行层"，"推理层"仍需云端支持。

展望：Apple 硬件路线图暗示 2 代内可运行 7B+ 模型，届时复合任务差距可能显著缩小。

## 关联

- [[orion-apple-neural-engine-llm]] — Apple Neural Engine 上的 LLM 推理，与 Foundation Models 互补
- [[gemma4-ondevice]] — 端侧模型能力基准
- [[edge-cloud-offloading]] — 端云协同的架构选择
- [[huoziime-ondevice-ime]] — 另一个端侧 LLM 应用场景（输入法）
- [[agent-persistent-identity]] — Agent 上下文保持问题的理论框架
