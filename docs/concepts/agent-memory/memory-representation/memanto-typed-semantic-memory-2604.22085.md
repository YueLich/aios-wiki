---
title: "Memanto: Typed Semantic Memory for LLM Agents"
arXiv: 2604.22085
date: 2026-04-26
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# Memanto: Typed Semantic Memory for LLM Agents

## 论文基本信息

- **作者**: Jinwei Ren, et al.
- **arXiv**: https://arxiv.org/abs/2604.22085
- **领域**: cs.AI, cs.CL

## 摘要

Memanto 提出为 LLM Agent 构建类型化语义记忆系统。现有 Agent 记忆通常是无类型的文本集合，缺乏结构化的语义组织，导致检索效率和可解释性受限。Memanto 引入类型化语义记忆，其中每个记忆条目都有显式类型标注（实体、事件、动作、信念等），支持类型感知的检索和推理。类型系统使 Agent 能够更高效地查询和推理记忆，支持"找所有关于 X 的信念"这类结构化查询。

## 核心贡献

1. **Typed Memory Architecture**: 首个为 LLM Agent 设计的类型化语义记忆架构
2. **Semantic Type System**: 定义实体、事件、动作、信念等记忆类型
3. **Type-aware Retrieval**: 支持类型过滤的结构化检索
4. **Memory Type Inference**: 自动推断新记忆的类型归属
5. **可解释性提升**: 类型化使记忆推理过程更可解释

## 研究背景与问题

文本型记忆缺乏语义结构，导致检索时难以精确过滤，推理时缺乏类型约束。Agent 记忆应该是"可推理的知识库"而非"文本的集合"。

## 核心方法

1. **Memory Type Schema**: 定义记忆类型的层级结构
2. **Type-annotated Memory Store**: 存储时即标注类型
3. **Type-aware Retriever**: 检索时支持类型过滤和类型约束推理
4. **LLM-based Type Inference**: 用 LLM 自动推断新记忆的类型
5. **Type-guided Reasoning**: 在推理时利用类型信息指导注意力分配

## 为什么重要

Memanto 将结构化知识图谱的思想引入 Agent 记忆，使记忆从"文本集合"进化为"可推理的类型化知识库"。这代表了 Agent 记忆系统的重要发展方向。

## 与移动端/端侧相关性

1. **高效类型过滤**: 类型化使端侧检索更高效，减少不必要的记忆加载
2. **结构化推理**: 类型约束使移动端推理更高效
3. **可解释记忆**: 移动端调试需要可解释的记忆系统
4. **隐私保护**: 类型化使选择性记忆访问控制更精细
