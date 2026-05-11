---
title: "WiCER: Wiki-memory Compile, Evaluate, Refine Iterative Knowledge Compilation for LLM Wiki Systems"
arXiv: 2605.07068
date: 2026-05-08
tags: [agent-memory, memory-representation, knowledge-compilation]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

The LLM Wiki pattern — compiling domain knowledge into a persistent artifact served to LLMs via KV cache inference — promises sub-second latency with zero retrieval failure. Realizing this requires solving the **compilation gap**: LLM compilation that distills raw documents into a wiki without catastrophically discarding critical facts. This paper characterizes the compilation gap across 17 RepLiQA domains (6,800 questions): full context KV cache inference outperforms RAG on curated knowledge (4.38 vs 4.08, 7.3× faster TTFT) but degrades below RAG at scale due to catastrophic fact omission during compilation.

## 核心贡献

1. **编译差距的系统刻画**：首次量化了 LLM Wiki 知识编译中的事实丢失问题，在 17 个 RepLiQA 领域、6800 个问题上验证
2. **RAG vs Wiki-KV 对比**：在精心策划的知识上，全上下文 KV cache 推理优于 RAG（4.38 vs 4.08，TTFT 快 7.3 倍），但在规模化时因编译过程中的灾难性事实遗漏而降级
3. **迭代编译-评估-细化框架**：提出 WiCER 迭代知识编译框架，Compile → Evaluate → Refine 循环逐步缩小编译差距
4. **事实级诊断**：能够识别哪些事实在编译过程中被遗漏，帮助精化编译策略

## 为什么重要

LLM Wiki 模式是 Agent 记忆的一种重要变体——将知识编译成持久化 artifact，通过 KV cache 直接提供，是实现"零检索失败"低延迟记忆系统的有前途方向。本文首次系统诊断了这个范式的核心瓶颈（编译差距），为后续改进提供了量化基线和迭代优化框架，对构建生产级 Wiki记忆系统有直接指导意义。

## 与移动端/端侧相关性

端侧 Agent 的本地知识库（如设备手册、个人笔记）可以采用 LLM Wiki 模式编译成本地 KV cache，实现极低延迟的本地知识访问。WiCER 的迭代编译-评估框架对在端侧资源受限环境下优化本地知识编译质量有直接价值。

## 参考文献

- arXiv: https://arxiv.org/abs/2605.07068
- Authors: Juan M. Huerta
