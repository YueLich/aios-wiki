---
title: "SEMA-RAG: A Self-Evolving Multi-Agent Retrieval-Augmented Generation Framework for Medical Reasoning"
arXiv: 2605.17101
date: 2026-05-16
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

检索增强生成（RAG）被广泛用于缓解医学问答中的幻觉和知识过时问题，但其主要单轮、静态检索范式与临床推理的多阶段过程不对齐。这种压缩的工作流导致两个结构性缺陷：问题到查询的转换往往缺乏临床基础的语义解释，检索缺乏迭代充分性反馈，难以形成可靠的证据链。本文认为这两个问题源于更深层原因：让单一推理链承担异构的解释、探索和裁决任务。解决方案是通过任务解耦和动态多轮探索重构工作流。

## 核心贡献

1. **自演进多 Agent RAG 框架**：将 RAG 分解为多个专业化 Agent（解释 Agent、探索 Agent、裁决 Agent），通过协作完成医学推理
2. **任务解耦机制**：将异构推理任务分离，使每个 Agent 专注于单一职责
3. **动态多轮探索**：引入迭代反馈循环，根据中间结果动态调整检索策略
4. **可靠证据链构建**：通过多 Agent 协作形成可追溯、可验证的医学推理链

## 为什么重要

医学问答是 Agent 记忆系统的重要应用场景——需要从大量医学文献中检索相关信息并综合推理。该框架通过多 Agent 协作解决了单 Agent RAG 的根本局限，对需要复杂推理的 Agent 系统有普遍参考价值。

## 与移动端/端侧的相关性

移动端健康顾问 Agent 需要在不依赖云端的情况下提供医学推理能力。SEMA-RAG 的多 Agent 架构可以分布式部署在端云协同环境中，敏感推理在端侧完成，知识密集型检索按需调用云端资源。
