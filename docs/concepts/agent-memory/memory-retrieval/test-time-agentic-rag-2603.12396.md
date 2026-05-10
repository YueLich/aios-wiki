---
title: "Test-Time Strategies for More Efficient and Accurate Agentic RAG"
arXiv: 2603.12396
date: 2026-03-12
tags: [agent-memory, memory-retrieval, agentic-rag]
reviewer: auto
source: arXiv RSS/API
---

# Test-Time Strategies for More Efficient and Accurate Agentic RAG

## 论文基本信息

- **标题**: Test-Time Strategies for More Efficient and Accurate Agentic RAG
- **arXiv ID**: 2603.12396
- **发表日期**: 2026-03-12
- **作者**: Brian Zhang, Deepti Guntur, Zhiyang Zuo, Abhinav Sharma, Shreyas Chaudhari, Wenlong Zhao, Franck Dernoncourt, Puneet Mathur, Ryan Rossi, Nedim Lipka
- **方向**: 记忆检索 · Agentic RAG
- **类别**: cs.IR

## 摘要（原文翻译）

检索增强生成（RAG）系统在处理复杂多跳问题时面临挑战，而 Search-R1 等智能体框架通过迭代操作已被提出以应对这些复杂性。然而，此类方法可能引入效率问题，包括重复检索已处理过的信息，以及在当前生成提示中有效上下文检索结果的困难。这些问题可能导致不必要的检索轮次、次优推理、不准确答案和 token 消耗增加。本文研究了对 Search-R1 流水线进行测试时修改，以减轻这些已识别的缺点。具体而言，探索了两个组件及其组合的集成：一个上下文压缩器和一个重放避免机制。

## 核心贡献

1. **上下文压缩器**：在每轮检索后将冗余信息压缩，减少重复检索对后续轮的干扰
2. **重放避免机制**：检测并跳过已检索过的内容块，避免重复检索开销
3. **组合策略**：将两个组件结合，在多跳问答基准上实现准确率提升 + token 消耗降低的双重收益

## 为什么重要

记忆系统在长期运行中容易积累重复/冗余信息，导致检索效率下降。重放问题在持续学习的记忆系统中尤为突出——当新记忆与旧记忆共享实体或事件时，系统可能反复检索同一内容。Test-Time 的压缩和去重策略可在不修改底层模型的情况下显著提升检索效率，对现有记忆系统具有即插即用的价值。

## 与移动端/端侧的相关性

- **高相关性**：减少 token 消耗直接降低移动端内存带宽和计算压力
- **实时去重**：避免重复检索的机制适合资源受限的端侧环境
- **可插拔**：上下文压缩器可作为现有 RAG/Memory 系统的独立模块使用

## 参考文献

- 原论文: https://arxiv.org/abs/2603.12396
