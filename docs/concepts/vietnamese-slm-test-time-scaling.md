---
type: concept
tags: [slm, test-time-scaling, vietnamese, qwen3, reasoning, on-device, constrained-devices, 端侧]
related: [[slms-vs-llms]], [[mini-cpm-242]], [[on-device-streaming-asr-compact]], [[efficient-reasoning-edge]], [[dharmaocr-specialized-slm-ocr]]
sources:
  - url: https://arxiv.org/abs/2604.17794
    title: "Bridging the Reasoning Gap in Vietnamese with Small Language Models via Test-Time Scaling"
    date: 2026-04-20
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# 越南语小语言模型的推理鸿沟修复：通过测试时缩放

> 在资源受限设备上部署 AI 推理能力是普适 AI 民主化的关键。本文研究 Qwen3-1.7B 在越南语数学推理中的"推理鸿沟"问题，发现基础模型拥有强大隐含知识（准确率 4.05/5.00）但受困于"格式化鸿沟"。通过测试时缩放（Test-Time Scaling）策略和越南语本地化推理数据集 Vi-S1K 来弥合这一鸿沟。

## 核心问题

小型语言模型（SLM）在非英语语言中面临严重的"推理鸿沟"（reasoning gap）：
- 在英语任务上表现尚可，但在越南语等低资源语言上难以维持连贯的思维链
- 这限制了端侧 AI 在非英语市场的实际可用性
- 测试时缩放策略能否帮助 SLM 在低资源语言上恢复推理能力？

## 方法架构

### Qwen3-1.7B + Test-Time Scaling

以 Qwen3-1.7B 架构为研究对象（1.7B 参数，适合端侧部署）：

1. **Vi-S1K 数据集**：通过 Gemini 2.5 Flash-Lite 驱动的管道本地化的高保真越南语推理数据集
   - 不是简单的翻译，而是经过验证的本地化推理链
   - 包含完整的解题步骤和中间推理过程

2. **Vi-Elementary-Bench**：双资源基准，用于严格评估越南语基础数学推理能力
   - 区分了"模型知道什么"和"模型能输出什么"

3. **LLM-as-a-Judge 评估协议**：使用大模型作为评判标准，避免人工评估的主观性

### 核心发现：格式化鸿沟

**基础模型的隐含知识 vs. 表达能力**：
- 准确率 4.05/5.00 — 模型"知道"正确答案
- 但输出格式和推理链表达存在严重问题 — "格式化鸿沟"（formatting gap）
- 模型内部有正确的推理能力，但无法有效组织成连贯的推理步骤

## 实验结果

关键定量结果：
- **隐含知识分数**：4.05/5.00（LLM-as-a-Judge 评估），说明模型内部确实掌握了越南语数学推理
- **格式化鸿沟**：基础模型在输出结构化推理链时表现严重下降
- **Test-Time Scaling 效果**：通过测试时缩放策略（可能包括多次采样、验证、重试等），可以显著弥合格式化鸿沟

## 关键洞察

**"知道但说不出来"现象**：SLM 在低资源语言中的核心问题不是知识缺失，而是表达能力的结构性缺陷。模型在内部表示层面已经"学会了"推理，但在解码阶段无法将这种能力转化为目标语言的结构化输出。

**Test-Time Scaling 的价值**：这个发现对端侧部署意义重大——不需要重新训练或增大模型，只需在推理阶段投入更多计算（多次采样、验证器、重试），就能显著提升质量。这正是端侧设备可以承受的（推理时多花几秒 vs. 重新训练需要数天）。

**小模型的"暗知识"**：1.7B 模型在越南语上的隐含知识分数（4.05/5）比预期高得多。这提示我们：很多端侧小模型可能被低估了——它们"知道"的远比"能表达"的多。

## 为什么重要

1. **端侧 AI 民主化**：为非英语市场（尤其是越南语等低资源语言）的端侧 AI 部署提供了技术基础
2. **Test-Time Scaling 范式**：证明了在不增大模型的前提下，通过推理时计算投入可以显著提升 SLM 性能——这完美契合端侧约束
3. **低资源语言评估基准**：Vi-Elementary-Bench 为其他低资源语言的 SLM 评估提供了方法论参考
4. **模型潜力评估**：隐含知识分数的方法论可以帮助评估端侧模型的"真实能力"而非"表面输出"

## 关联
- [[slms-vs-llms]] — 小模型 vs 大模型的综合对比
- [[mini-cpm-242]] — 另一款注重效率的端侧小模型
- [[on-device-streaming-asr-compact]] — 端侧语音识别的压缩优化，类似的资源受限部署
- [[efficient-reasoning-edge]] — 边缘设备上的高效推理方法
- [[dharmaocr-specialized-slm-ocr]] — 专用小模型在 OCR 场景的端侧应用
