---
title: "Storage Is Not Memory: A Retrieval-Centered Architecture for Agent Recall"
arXiv: 2605.04897
date: 2026-05-06
tags: [agent-memory, memory-retrieval, architecture, sqlite, benchmarks]
reviewer: auto
source: arXiv API
---

# Storage Is Not Memory: A Retrieval-Centered Architecture for Agent Recall

**作者:** Joshua Adler, Guy Zehavi
**发表:** 2026-05-06
**方向:** 记忆检索 / 系统架构 / 基准评测

## 摘要

当前 Agent 记忆系统将"提取"（extraction）作为摄取阶段的核心原语——在不知道查询的情况下预先丢弃内容，导致检索时无法恢复关键信息。本文认为这是错误的抽象层次。提出 **True Memory**，一种六层架构，将系统中心从存储模式转向多阶段检索管道，对原始事件完整保留。完整系统在普通 CPU 上以单个 SQLite 文件运行，无需外部数据库、向量索引、图存储或 GPU。

在 LoCoMo（1540 道题，10 个多会话对话）上，True Memory Pro 达到 93.0% 准确率（3 次平均），对比 Mem0 的 61.4%、Supermemory 的 65.4%、Zep 的约 71%、EverMemOS 的 94.5%（在相同 gpt-4.1-mini 答题模型下）。在 LongMemEval（500 道题）上达到 87.8%。在 BEAM-1M（百万 token 规模，700 道题）上达到 76.6%，超过此前已发表的最佳结果 Hindsight 的 73.9%。56 配置消融实验表明顶级配置家族的性能差距仅为 1.3 个百分点。

## 核心貢獻

1. **六层检索中心架构**：将系统中心从"存储模式"转向"多阶段检索管道"，原始事件完整保留verbatim
2. **SQLite 单文件部署**：无需外部数据库、向量索引、图存储或 GPU，适合端侧/边缘部署
3. **全面基准对比**：在 LoCoMo、LongMemEval、BEAM-1M 三个基准上系统性对比 Mem0、Supermemory、Zep、EverMemOS、Hindsight 等系统
4. **摄取 vs 检索解耦**：明确区分"提取时机"与"检索时机"，批评当前系统过早丢弃信息的做法
5. **56 配置消融**：覆盖 top-performing 配置家族的 1.3pp 差距，表明特定设计选择对最终性能影响相对有限

## 技術細節

### 六层架构（True Memory）

| 层次 | 功能 |
|------|------|
| L1: Event Preservation | 原始事件 verbatim 存储，不做预提取 |
| L2: Incremental Indexing | 轻量级增量索引，支持高效检索 |
| L3: Multi-Stage Retrieval | 多阶段检索管道，逐步精炼结果 |
| L4: Query Decomposition | 查询分解，处理复杂多跳问题 |
| L5: Answer Synthesis | 答案综合，整合多片段记忆 |
| L6: Verification | 答案验证，确保事实一致性 |

### 关键洞察

> **"Extraction at ingestion is the wrong primitive"** — 在不知道查询的情况下决定丢弃什么，本质上是一个无法正确解答的问题。

当前主流系统（Mem0、Supermemory、Zep）在摄取阶段做信息提取/压缩/摘要，但这些决策依赖于当时的认知，无法预测未来的查询需求。True Memory 的核心转变：将信息保留推迟到检索阶段，让查询上下文指导信息组织。

### 基准结果汇总

| 基准 | True Memory Pro | Mem0 | Supermemory | Zep | EverMemOS | Hindsight |
|------|----------------|------|-------------|-----|-----------|----------|
| LoCoMo (93.0%*) | **93.0%** | 61.4% | 65.4% | ~71% | 94.5% | — |
| LongMemEval | **87.8%** | — | — | — | — | — |
| BEAM-1M | **76.6%** | — | — | — | — | 73.9% |

*3-run mean, gpt-4.1-mini answer model matched

## 為什麼重要

1. **架构范式转变**：将记忆系统从"存储中心"转向"检索中心"，这是记忆系统设计思想的根本性反思
2. **工程实用性**：SQLite 单文件、无 GPU、无外部依赖，使得在移动端/边缘设备部署变得极其简单
3. **基准透明度**：对现有商业系统（Mem0、Zep 等）的公平对比，揭示了当前系统的真实能力边界
4. **反直觉发现**：Pretrained 系统（Mem0、Supermemory）表现不如 True Memory 的轻量方法，说明摄取策略比模型规模更重要

## 與端側/移動端相關性

1. **SQLite 部署**：无需任何外部服务，单文件可在手机、手表、IoT 设备上直接运行
2. **零向量索引依赖**：避免了 HNSW/PQ 等复杂向量索引的内存和计算开销
3. **CPU-only**：适合移动端有限的算力预算，实测在 commodity CPU 上即可达到 SOTA
4. **多会话对话记忆**：直接面向个人助手应用场景，需要跨会话保持上下文一致性

## 参考文献

- Mem0: https://mem0.dev
- Supermemory: https://supermemory.ai
- Zep: https://www.zep.com
- EverMemOS: prior published system
- Hindsight: BEAM-1M prior state-of-the-art (73.9%)
- LoCoMo Benchmark: 1540 questions, 10 multi-session conversations
- LongMemEval: 500 questions
- BEAM-1M: 700 questions at 1-million-token scale
