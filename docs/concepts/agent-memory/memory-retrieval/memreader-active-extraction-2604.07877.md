---
title: "MemReader: From Passive to Active Extraction for Long-Term Agent Memory"
arXiv: 2604.07877
date: 2026-04-09
tags: [agent-memory, memory-retrieval, memory-writing, active-learning]
reviewer: auto
source: arXiv API
authors: "Jingyi Kang, Chunyu Li, Ding Chen, Bo Tang, Feiyu Xiong, Zhiyu Li"
---

## 论文信息

- **arXiv**: 2604.07877
- **发表日期**: 2026-04-09
- **作者**: Jingyi Kang, Chunyu Li, Ding Chen, Bo Tang, Feiyu Xiong, Zhiyu Li
- **方向**: 记忆检索与写入

## 摘要

长期记忆对个性化 Agent 至关重要，但填充记忆始终是瓶颈。现有系统将记忆提取视为从上下文到结构化条目的单次被动转录，难以应对嘈杂对话、缺失引用和跨轮依赖，导致记忆污染、低价值写入和不一致。本文提出 MemReader 系列——Agent 系统主动长期记忆提取器：MemReader-0.6B，一个紧凑、性价比高的被动提取器，用于准确、模式一致的结构化输出；MemReader-4B，一个通过 GRPO（群体相对策略优化）优化的主动提取器，在 ReAct 风格范式下显式评估信息价值、引用模糊性和完整性，可选择性写入记忆、延迟不完整输入、检索历史上下文或丢弃无关闲聊。在 LOCOMO、LongMemEval 和 HaluMem 上的实验表明，MemReader 始终超越基于提取的基线。MemReader-4B 在知识更新、时间推理和幻觉减少任务上达到最新最优。MemReader 已集成到 MemOS 并正在实际应用中部署。

## 核心贡献

1. **主动记忆提取范式**：从被动转录转向主动决策——评估信息价值后再决定是否写入
2. **MemReader 双模型系列**：0.6B 被动提取器（高效）+ 4B 主动提取器（决策能力）
3. **GRPO 优化**：通过群体相对策略优化让模型学会"何时写、何时跳过"
4. **模式一致性**：结构化输出确保记忆条目格式统一，支持可靠检索

## 为什么重要

记忆写入是记忆系统的第一道关口——无差别地写入所有内容只会导致"记忆污染"，而 MemReader 证明了"选择性写入"的价值。这对资源受限的端侧设备尤为重要：写入的每一条记忆都占用存储和后续检索成本。

### 与移动端/端侧的相关性

- **0.6B 模型**可在移动端运行，实现本地记忆提取
- **选择性写入**对存储受限的端侧设备至关重要
- 已集成到 **MemOS** 实际部署

## 延伸阅读

- LoCoMo Benchmark
- LongMemEval Benchmark
- HaluMem Benchmark
- MemOS Memory Operating System
