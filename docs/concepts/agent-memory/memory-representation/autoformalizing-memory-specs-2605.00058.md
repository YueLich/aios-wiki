---
title: "Autoformalizing Memory Specifications with Agents"
arXiv: 2605.00058
date: 2026-05-01
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Jan Ole Ernst, Dmitri Michelangelo Saberi, Derek Christ, Thomas Zimmermann, Rajath Salegame, Suhaas M. Bhat, Stanislav Levental, Thomas Dybdahl Ahle, Matthias Jung
- **提交日期**: 2026-05-01

## 摘要

The primary goal of Design Verification (DV) is to ensure that a proposed chip design implementation (either in code, or physical form) exactly matches its specification and is free of functional errors. This paper studies how LLM agents can maintain and query formal memory specifications in DV workflows. The key challenge is that specifications exist in both natural language (informal) and formal languages (e.g., SystemVerilog Assertions). The agent must reason across both representations. The paper proposes an autoformalization approach where the agent maintains a dual memory: informal specifications in a vector store and formal specifications in an SMT-solver-compatible format. When the agent queries the design (e.g., "does module X meet its timing constraints?"), it retrieves relevant spec fragments from both representations and uses the formal query for rigorous verification.

## 核心贡献

1. **双重记忆表示**: 自然语言规格（向量存储）和形式化规格（SMT 可解格式）并存
2. **跨表示推理**: 查询时从两种表示中检索片段，形式化部分用于严格验证
3. **硬件记忆正确性**: 填补设计验证中形式化方法与自然语言意图之间的空白

## 为什么重要

为 LLM Agent 引入形式化验证能力提供了记忆系统层面的解决方案，对于安全关键的硬件设计验证具有重要意义。

## 与端侧/移动端的相关性

SMT solver 通常较重，端侧部署需要轻量近似或预验证模板库。适用于边缘芯片设计工作站，不适合资源极度受限的端侧设备。
