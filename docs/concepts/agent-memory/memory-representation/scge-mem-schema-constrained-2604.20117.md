---
title: "SCG-MEM: Schema-Constrained Generation for Agent Memory"
arXiv: 2604.20117
date: 2026-04-22
authors: ["Lei Zheng", "Weinan Song", "Daili Li", "Yanming Yang"]
tags: [agent-memory, memory-representation, schema, generative-memory]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.20117
- **发表日期**: 2026-04-22
- **作者**: Lei Zheng, Weinan Song, Daili Li, Yanming Yang
- **方向**: 记忆表示（Schema约束生成）

## 摘要

**背景问题**：现有 Agent 记忆系统大多基于密集检索（dense retrieval），但检索高度依赖句子内的语义重叠或实体匹配。当实例语义相似但上下文不同时，嵌入向量难以区分，导致检索到大量上下文错配的条目。另一方面，直接使用开放式生成进行记忆访问存在"结构幻觉"风险——模型生成的记忆键在记忆中根本不存在，导致查找失败。

**核心方法**：本文从建构主义认识论（constructivist epistemology）出发，提出记忆本质上由认知 schema 组织，有效的 recall 必须是在这些图式结构内执行的生成过程。据此提出 SCG-MEM（Schema-Constrained Generative Memory）架构：
1. **认知 Schema**：维护动态认知 Schema，严格约束 LLM 解码仅生成有效的记忆条目键，从形式上防止结构幻觉
2. **记忆更新**：通过同化（assimilation，将输入锚定到现有 schema）和顺应（accommodation，用新概念扩展 schema）支持长期适应
3. **联想图（Associative Graph）**：通过激活传播实现多跳推理

实验在 LoCoMo 基准上表明，SCG-MEM 在所有类别上均显著优于检索基线。

## 核心贡献

1. **Schema约束的生成式记忆访问**：将记忆访问重新表述为 Schema 约束的生成过程，为结构幻觉提供形式化保证
2. **双重适应机制**：同化+顺应机制使记忆系统能够动态适应新概念，同时保持与已有知识的一致性
3. **联想图多跳推理**：通过激活传播实现跨记忆条目的多跳推理，而非简单匹配
4. **LoCoMo 基准验证**：在真实基准上全面超越检索式记忆系统

## 为什么重要

当前大多数 Agent 记忆系统依赖向量检索，但这本质上是"记忆复制"而非"记忆建构"。SCG-MEM 首次将建构主义认识论形式化地引入 Agent 记忆架构，提出记忆访问必须是受 schema 约束的生成过程。这一范式转变——从被动检索到主动建构——对下一代记忆系统的设计具有深远影响：

- **防止幻觉**：通过 schema 约束从根本上消除不存在的记忆键
- **支持自适应**：同化/顺应机制使记忆随使用不断优化
- **可解释性强**：schema 结构使记忆组织可审计、可干预

## 与端侧/移动端的相关性

Schema 约束的生成比全空间向量检索更高效——解码空间被约束到有效键集合，而非全部词表。对于移动端 LLM Agent，SCG-MEM 的 schema 树结构支持增量索引和分层检索，适合内存和算力受限的设备。schema 的显式结构也降低了记忆读取的推理成本。

## 参考文献

- arXiv: 2604.20117 | https://arxiv.org/abs/2604.20117
