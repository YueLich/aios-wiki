---
title: "To Know is to Construct: Schema-Constrained Generation for Agent Memory"
arXiv: 2604.20117
date: 2026-04-22
tags: [agent-memory, memory-representation, schema, generative-memory]
reviewer: auto
source: arXiv RSS/API
---

# To Know is to Construct: Schema-Constrained Generation for Agent Memory

## 论文基本信息

- **arXiv ID**: 2604.20117
- **作者**: (From paper)
- **提交日期**: 2026-04-22
- **类别**: cs.CL, cs.AI

## 摘要

Constructivist epistemology argues that knowledge is actively constructed rather than passively copied. Despite the generative nature of Large Language Models (LLMs), most existing agent memory systems are still based on dense retrieval. However, dense retrieval heavily relies on semantic overlap or entity matching within sentences. Consequently, embeddings often fail to distinguish instances that are semantically similar but contextually distinct, introducing substantial noise by retrieving context-mismatched entries. Conversely, directly employing open-ended generation for memory access risks "Structural Hallucination" where the model generates memory keys that do not exist in the memory, leading to lookup failures. Inspired by this epistemology, we posit that memory is fundamentally organized by cognitive schemas, and valid recall must be a generative process performed within these schematic structures. To realize this, we propose SCG-MEM, a schema-constrained generative memory architecture. SCG-MEM reformulates memory access as Schema-Constrained Generation. By maintaining a dynamic Cognitive Schema, we strictly constrain LLM decoding to generate only valid memory entry keys, providing a formal guarantee against structural hallucinations. To support long-term adaptation, we model memory updates via assimilation (grounding inputs into existing schemas) and accommodation (expanding schemas with novel concepts). Furthermore, we construct an Associative Graph to enable multi-hop reasoning through activation propagation. Experiments on the LoCoMo benchmark show that SCG-MEM substantially improves performance across all categories over retrieval-based baselines.

## 核心贡献

1. **建构主义认知框架**：将记忆访问重新定义为「在图式约束内的生成过程」而非检索。
2. **结构幻觉的形式化保证**：通过动态认知图式严格约束 LLM 解码，只生成有效的记忆键。
3. **记忆更新双模式**：吸收（assimilation）将新输入纳入现有图式；顺应（accommodation）扩展图式容纳新概念。
4. **关联图支持多跳推理**：通过激活传播实现多跳推理能力。

## 为什么重要

SCG-MEM 解决了传统密集检索的根本问题：语义相似的实例在上下文中可能截然不同，导致检索噪声。生成式记忆访问虽有潜力，但开放域生成面临「结构幻觉」风险（生成的记忆键在记忆中不存在）。SCG-MEM 通过图式约束在生成式范式下提供了形式化保证，在 LoCoMo 所有类别上显著超越检索基线。

## 与移动端/端侧相关性

- 认知图式与移动端 App 场景模型高度契合——App 操作有明确的层级结构
- 形式化保证对高风险移动操作（如支付、删除）尤为重要
- 关联图多跳推理适合移动端复杂工作流
- 图式压缩表示比完整向量库更节省存储
