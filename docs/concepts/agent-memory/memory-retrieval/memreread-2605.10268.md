---
title: MemReread: Enhancing Agentic Long-Context Reasoning via Memory-Guided Rereading
arXiv: 2605.10268
date: 2026-05-11
tags: [agent-memory, memory-retrieval, long-context]
reviewer: auto
source: arXiv API
---

## 摘要

本文针对**线性记忆读写范式**（memorize-while-reading）在长上下文推理中的潜在信息丢失问题，提出了**Memory-Guided Rereading**机制。当前的基于记忆的 Agent 在线性处理文档块时动态更新记忆，但之前丢弃的潜在证据难以恢复。引入检索模块虽允许 Agent 回忆先前被覆盖的信息，但现有方法未能有效指导何时以及如何触发重读。MemReread 通过**记忆引导的重读策略**增强 Agent 的长上下文推理能力，在保持线性复杂度优势的同时显著提升推理质量。

## 核心贡献

1. **Memory-Guided Rereading 机制**：提出一种由记忆状态引导的主动重读策略，在首次阅读时记录关键记忆线索，触发对潜在证据区域的精准重读。
2. **记忆覆盖问题的系统性解决**：针对"记忆写入时丢弃潜在证据"这一核心问题，设计了基于记忆置信度的重读触发器，无需遍历全部上下文。
3. **线性复杂度保持**：方法在 O(n) 线性复杂度下运行，不引入二次 attention 开销，适合长文档处理。
4. **多跳推理任务验证**：在多跳问答和长距离依赖推理任务上显著优于基线方法。

## 方法详解

MemReread 的核心思想是：当记忆被更新时，系统会评估当前记忆的**置信度/完整性分数**，当分数低于阈值时，触发对历史文档块的重读。具体包括：

- **记忆线索编码**（Memory Cue Encoding）：首次阅读时，为每个文档块生成记忆线索向量，用于后续重读定位。
- **置信度评估**（Confidence Assessment）：基于当前记忆状态与查询的相关性计算置信度。
- **选择性重读**（Selective Rereading）：仅重读与低置信度区域相关的文档块，而非全量重读。

## 为什么重要

长上下文推理是 Agent 系统的核心能力之一。传统方法要么使用 full attention（O(n²) 复杂度），要么使用简单的记忆覆盖策略（信息丢失）。MemReread 在两者之间取得平衡，通过记忆引导的智能重读，在不显著增加计算开销的前提下恢复丢失的关键证据。这对**端侧部署的长上下文 Agent**（如手机上的个人助手）具有直接的实用价值。

## 与移动端/端侧相关性

- **低计算开销**：线性复杂度设计，适合移动端 GPU/NPU 资源受限场景
- **增量式记忆更新**：无需全量重读文档，适合移动设备上的流式数据处理
- **隐私友好**：记忆本地存储，推理过程不涉及云端通信
- **适合可穿戴设备**：轻量级记忆机制，适合智能手表等受限设备的长期任务跟踪

## 参考文献

- Ji, B., et al. (2026). MemReread: Enhancing Agentic Long-Context Reasoning via Memory-Guided Rereading. arXiv:2605.10268.
