---
type: concept
tags: [on-device, cloud-inference, agentic-tool-calling, ios, foundation-models, comparison, 智能体]
related: [[clawmobile-agentic]], [[edge-cloud-offloading]], [[edgeflow-cold-start]], [[sustainability-ondevice-intelligence]], [[gemma4-ondevice]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://subralabs.com/lab/on-device-vs-cloud-llm.html
    title: "On-Device vs Cloud LLMs for Agentic Tool Calling"
    date: 2026-04-15
    reliability: high
created: 2026-04-15
updated: 2026-04-15
---

# 端侧 vs 云端 LLM：Agentic 工具调用的实战对比

> 基于真实 iOS 旅行礼宾 App 的 3B（Apple Foundation Models）vs 20B（GPT-OSS via OpenRouter）对比实验，由 SubraLabs 于 2026 年 4 月发布。

## 核心问题

端侧 LLM 在实际 agentic 工具调用场景中到底够不够用？这不是理论问题——当你需要模型**搜索、过滤、组合结果并生成自然语言回答**时，3B 模型能否胜任？

## 实验设置

**应用场景**：度假村目录 iOS App 的 AI 礼宾功能，需要：
1. 在 ~85 个物业数据集上执行自由文本搜索
2. 结构化过滤（区域、价格、评分、设施）
3. 基于 Haversine 距离的附近机场查找
4. 以意大利语生成一致的人设风格回答

**三个工具**：
- `searchHotels` — 自由文本搜索
- `applyFilters` — 结构化过滤
- `searchHotelsNearAirport` — 五个机场的距离查找

**核心挑战**：不是单次工具调用，而是**复合任务**——需要多次串行调用工具、解读部分结果、编织成连贯的自然语言回答（reason → act → synthesise 循环）。

## 关键发现

### 发现 1：工具调用复杂度是瓶颈

3B 端侧模型可以正确识别要调用哪个工具并生成合法参数。**但在复合任务上持续失败**：

| 失败模式 | 具体表现 |
|---------|---------|
| 数数错误 | 工具返回 2 个结果，模型说 "这里有 3 个"，然后正确列出 2 个 |
| 自我矛盾 | 模型说 "没找到匹配的"，紧接着展示有效结果 |
| 对话上下文丢失 | "那几个里面哪些有泳池？"触发全新搜索而非在前次结果上过滤 |

**这不是 prompt engineering 问题，是参数量问题。** 多种 prompt 策略（CoT、分离 decide/respond、few-shot）都无法可靠解决。

GPT-OSS 20B 则轻松处理了复合任务，正确解释工具结果、计数、上下文化，并以自然的意大利语 + 礼宾人设输出。

### 发现 2：响应质量与语言差异

| 维度 | 端侧 3B | 云端 20B |
|------|---------|---------|
| 人格一致性 | ❌ 无法维持 | ✅ 知识渊博的旅行顾问 |
| 隐含意图理解 | ❌ 字面理解 | ✅ "放松"→水疗评分+环境评分 |
| 意大利语质量 | 语法正确但缺质感 | 自然且语域恰当 |
| 交互感受 | 数据库导出 | 有见识的朋友建议 |

### 发现 3：成本不是你想象的门槛

| 指标 | 值 |
|------|-----|
| 每 100K tokens 成本（混合 I/O） | $0.005 - $0.007 |
| 平均对话（5 轮） | ~8K-12K tokens |
| 每对话成本 | < $0.001 |
| 1000 对话/月 | ~$0.50-$0.70 |

**月成本低于一个 App Store 订阅。** 云端推理成本已低到可以完全吸收进免费增值模型。

## 端侧 vs 云端权衡矩阵

| 维度 | 端侧 (~3B) | 云端 (20B) |
|------|-----------|-----------|
| 简单工具调用 | ✅ 可用 | ✅ 可用 |
| 复合 Agent 任务 | ❌ 不可靠 | ✅ 可靠 |
| 响应连贯性 | 功能性 | 自然 |
| 非英语质量 | 可接受 | 强 |
| 隐私 | 完全本地 | 需信任提供商 |
| 延迟 | 首 token 即时 | 可接受（流式） |
| 离线能力 | 完全支持 | 无 |
| 设备要求 | 新硬件 + Apple Intelligence | 任何有网设备 |
| 每对话成本 | $0 | < $0.001 |

## 实践决策框架

**使用端侧**：任务为单步、模型输出可直接消费（分类、提取、摘要、单次简单工具调用）

**使用云端**：任务需要多步推理、工具编排、人设一致性、或强非英语生成

**提供两者 + 用户切换**：当用户群中有隐私优先者、或需要离线降级时

> 实际做法：默认云端（质量优先），端侧作为可选开关，让用户在隐私和能力之间自选。

## 未来展望

Apple 硬件轨迹表明 **2 代内设备可跑 7B+ 模型**，届时复合任务差距可能大幅缩小。在此之前，agentic iOS 功能的务实策略是：**构建后端无关的工具调用基础设施，默认云端，保留端侧路径待模型追上**。

## 关联

- [[clawmobile-agentic]] — 同样涉及移动端 Agent 系统的工具编排挑战
- [[edge-cloud-offloading]] — 端云协作的 Router 架构可解决此处发现的能力边界
- [[edgeflow-cold-start]] — 端侧模型冷启动优化可改善首 token 延迟
- [[sustainability-ondevice-intelligence]] — 端侧推理的性能/能耗/隐私权衡
- [[gemma4-ondevice]] — Gemma 4 的端侧能力是否能突破 3B 的复合任务瓶颈
- [[on-device-inference-memory-pressure]] — 端侧模型的内存压力管理
