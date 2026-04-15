---
type: concept
tags: [推理优化, inference, self-assessment, routing, mobile-llm, on-device]
related: [[exectune-guide-core-policy]], [[edgeflow-cold-start]], [[kv-cache-quantization-ondevice]], [[septq-post-training-quantization]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2604.12634
    title: "RPRA: Predicting an LLM-Judge for Efficient but Performant Inference"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# RPRA: 预测 LLM-Judge 实现高效推理

> 让小型端侧模型在生成回答前"自知"能否回答好，从而只在必要时路由到大型云端模型——节省 70%+ 的推理成本。

## 核心问题

LLM 在消费设备上面临根本性的效率-质量权衡：主流 LLM 需要 TB 级 GPU 内存，而 ChatGPT 每天处理超过 25 亿次 API 请求。小型模型（如 MobileLLM 0.9B）在某些数据集上可媲美大模型，但在其他任务上性能骤降且表现不稳定（如著名的"how many Rs in strawberry"错误）。问题在于：**小模型不知道自己什么时候能答好、什么时候会犯错**。

## 方法架构

论文提出两个范式：

### PA (Predict-Answer)
模型在生成回答前，预测 LLM Judge 会给自己的回答打多少分。如果预测低分，则路由到大模型。

### RPRA (Reason-Predict-Reason-Answer)
在 PA 基础上增加了两轮推理：先推理再预测分数，再推理再回答。这个多步推理结构让模型更准确地评估自身能力。

### 两种实现路径

**Report Card 系统**（零训练）：
- 在多个数据集上评估模型的历史表现
- 用 LLM Judge 的评分构建性能摘要（report card）
- 推理时将 report card 作为上下文提供给模型
- 适用于任何模型，包括闭源系统

**后见之明微调**（Hindsight Trick）：
- 使用 Andrychowicz et al. (2017) 的 hindsight trick 构造训练数据
- 用 Judge 评分重新标注样本
- 对 MobileLLM 0.9B、Llama 3.1 8B、Llama 3.2 1B/3B 进行 SFT
- 消除推理时处理 report card tokens 的开销

## 实验结果

### 模型覆盖
评估了 MobileLLM 0.9B、Llama 3.1 8B、Llama 3.2 1B/3B、Llama 3.3 70B、GPT OSS 20B/120B、DeepSeek Distilled 系列、Llama 4 Scout 等模型。

### 关键发现

| 发现 | 详情 |
|------|------|
| 大模型零样本自评能力好 | 特别是推理模型，能较准确预测 Judge 评分 |
| 小模型存在校准问题 | 要么过度自信，要么过度不自信 |
| Report Card 显著提升小模型 | 无需训练即可大幅改善预测准确度 |
| 更难的问题自知更强 | 模型在困难查询上表现更好的自我意识 |
| Hindsight 微调效果好 | 无需 report card token 开销，预测性能强劲 |

### 移动端意义
- **路由优化**：端侧小模型在确认能力匹配时直接回答，否则路由云端
- **成本节省**：避免对简单查询也调用大模型，节省 70%+ 推算成本
- **延迟降低**：本地快速响应简单查询，只有复杂任务才产生云端延迟
- **不需要复杂架构**：Report Card 零训练可用，微调用标准 SFT 即可

## 关键洞察

1. **自知是推理的前提**：小模型最大的问题不是"能力不够"而是"不知道自己什么时候够"。RPRA 解决的是元认知问题。
2. **难度作为信号**：模型在更难的问题上反而有更好的自我意识——这暗示难度感知可以作为路由的辅助信号。
3. **Report Card 是通用方案**：不需要修改模型架构，只需在推理时提供历史性能数据。这对闭源模型和 API 服务特别有价值。
4. **与 ExecTune 互补**：ExecTune 用 Guide Model 从外部控制 LLM 行为，RPRA 让模型从内部评估自身能力。两者可以结合——先自评，再用 Guide Model 微调。

## 为什么重要

手机端 AI 的核心挑战之一是"端云协同"——什么时候用端侧模型，什么时候调云端。RPRA 提供了一种**数据驱动的自适应路由**方案：不是基于固定的规则或任务类型，而是让模型自己判断"这个查询我能答好吗？"这对端侧 Agent 至关重要——Agent 需要动态决定哪些工具/查询在本地处理，哪些需要云端支持。

## 关联
- [[exectune-guide-core-policy]] — Guide Model 从外部控制 LLM 输出，RPRA 从内部评估能力，两者可结合
- [[edgeflow-cold-start]] — EdgeFlow 减少端侧 LLM 冷启动延迟，RPRA 减少不必要的端云切换
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化降低端侧内存，RPRA 优化端云路由
- [[septq-post-training-quantization]] — 量化让小模型更小更快，RPRA 让小模型更"自知"
- [[on-device-inference-memory-pressure]] — 内存压力下小模型的可靠性问题正是 RPRA 要解决的
