---
type: concept
tags: [on-device, cloud, agentic, tool-calling, ios, apple, inference, 端侧推理, Agent]
related: [[apple-intelligence]], [[coremltools-9]], [[gemma4-ondevice]], [[clawmobile-agentic]]
sources:
  - url: https://subralabs.com/lab/on-device-vs-cloud-llm.html
    title: "On-Device vs Cloud LLMs for Agentic Tool Calling in a Real iOS App"
    date: 2026-04
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# 端侧 vs 云端 LLM：真实iOS应用中的Agent工具调用对比

> SubraLabs在iOS度假搜索应用中对比Apple端侧Foundation Models（~3B）与GPT-OSS 20B（云端）的Agent工具调用能力。核心发现：3B模型的瓶颈不是"能不能调工具"，而是"能不能正确理解和整合工具返回的结果"。

## 核心问题

当端侧LLM（如Apple Foundation Models的3B模型）执行Agent工具调用时：
- 能否正确识别要调用的工具？
- 能否正确解释工具返回的结果？
- 能否在多步骤推理中保持上下文连贯？
- 是否在所有场景下都足够可用？

## 方法/架构

### 测试场景
一个iOS度假搜索应用，需要Agent执行三步循环：**reason（推理）→ act（执行）→ synthesise（整合）**：

1. **searchHotels** — 自由文本搜索（名称、位置、标签）
2. **applyFilters** — 结构化过滤（区域、价格、评分、设施）
3. **searchHotelsNearAirport** — 基于机场距离的搜索

**关键复杂度**：不是单次工具调用，而是多步链式调用 + 结果理解 + 自然语言合成。响应语言为意大利语，需要保持度假顾问人格。

### 对比方案
- **端侧**：Apple Foundation Models（~3B参数，iOS 26原生，支持@Generable结构化输出）
- **云端**：GPT-OSS 20B via OpenRouter（SSE流式传输，工具调用在本地执行）

## 实验结果/关键数据

### Finding #1: 工具调用复杂度是瓶颈

3B模型**能正确识别工具和生成有效参数**。问题出现在复合任务：

| 失败模式 | 示例 |
|---------|------|
| 计数错误 | 工具返回2个结果，模型说"有3个匹配"并列出正确的2个 |
| 自我否定 | 正确呈现结果后说"没找到符合条件的" |
| 上文丢失 | 用户追问"哪些有泳池？"时触发全新搜索而非过滤已有结果 |

尝试过的修复方法（均失败）：
- Chain-of-thought提示
- 分离"决策"和"响应"阶段
- Few-shot示例
- 极简系统提示

**结论**：这不是提示工程问题，是参数规模问题。GPT-OSS 20B处理这些复合任务毫无困难。

### Finding #2: 响应质量和语言

云端模型在多语言场景下表现显著更优：
- 端侧模型偶尔切换语言或输出不自然的翻译腔
- 云端模型保持一致的度假顾问人格和地道的意大利语

### Finding #3: 延迟对比

| 指标 | 端侧（3B） | 云端（20B） |
|------|-----------|------------|
| 首token延迟 | ~0ms | ~200-500ms |
| 完整响应 | 3-8秒 | 2-5秒 |
| 网络依赖 | 无 | 必需 |

端侧模型虽然"零首token延迟"，但因为需要更长的思考时间，整体响应时间与云端相当甚至更慢。

## 关键洞察

**"能调工具"≠"能做好Agent"**：端侧3B模型可以正确执行单次工具调用，但在多步推理、结果理解和上下文维护上表现不足。这说明端侧Agent的评估不能仅看"工具调用成功率"，还要看"复合任务完成质量"。

**参数规模的硬边界**：在当前技术水平下，3B模型在复杂Agent任务上存在明确的能力天花板。这不意味着端侧不可行，而是需要：
1. 针对Agent任务进行专门微调
2. 将复杂任务拆分为更简单的子任务
3. 使用云端作为"困难任务"的fallback（[[android-hybrid-inference]]）

**离线≠首选**：虽然端侧模型支持完全离线运行，但在网络可用时，云端20B的性价比更高。端侧更适合作为**离线备份**或**隐私敏感场景**的首选。

**对端侧Agent架构的启示**：
- 3B模型适合**单步工具调用**场景（搜索、过滤等简单操作）
- 复杂Agent流程需要更大的模型或[[clawmobile-agentic]]中的专门架构
- 混合部署是当前最优解：端侧处理简单任务，云端处理复杂推理

## 为什么重要

这是第一个在真实iOS应用中对比端侧和云端LLM的Agent工具调用能力的实证研究。它量化了端侧模型在Agent场景下的能力边界，对以下决策有直接指导意义：

1. **端侧Agent的适用场景**：单步工具调用 ✓，多步复合推理 ✗
2. **混合架构的必要性**：端侧+云端的[[android-hybrid-inference]]方案在Agent场景下尤为必要
3. **Apple Foundation Models的定位**：3B模型是"够用的起点"，但不是Agent复杂推理的解决方案

## 关联
- [[apple-intelligence]] — Apple端侧AI生态的核心组件，Foundation Models框架是其推理引擎
- [[coremltools-9]] — Core ML工具链，用于模型部署和优化
- [[gemma4-ondevice]] — Google的端侧模型，规模更大但部署方式不同
- [[clawmobile-agentic]] — 原生Agent架构设计，讨论了如何在移动端实现可靠Agent
- [[android-hybrid-inference]] — 端云混合推理模式，本文的研究结果支持这种架构选择
