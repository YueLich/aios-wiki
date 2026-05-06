---
title: "Goal-Directed Search Outperforms Goal-Agnostic Memory Compression in Long-Context Memory Tasks"
arXiv: 2511.21726
date: 2025-11-26
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Goal-Directed Search Outperforms Goal-Agnostic Memory Compression in Long-Context Memory Tasks

## 论文基本信息

- **作者**: Yicong Zheng, Kevin L. McKee, Thomas Miconi
- **arXiv**: https://arxiv.org/abs/2511.21726
- **领域**: cs.AI, cs.CL

## 摘要

长期记忆任务中，记忆压缩和目标导向搜索是两种主流范式。该论文系统比较了两种方法在需要长程记忆的 LLM 任务上的表现。出人意料的是，目标导向搜索（在需要时主动检索相关记忆）始终优于目标无关的记忆压缩（在推理前预先压缩所有历史）。分析表明，压缩-based 方法存在"压缩盲点"问题——被压缩掉的信息恰恰在某些查询中不可或缺。目标导向搜索通过按需检索避免了这一问题。

## 核心贡献

1. **系统性比较研究**: 首次系统比较目标导向搜索 vs 记忆压缩在长记忆任务上的效果
2. **压缩盲点发现**: 发现压缩-based 方法存在固有的"压缩盲点"问题
3. **按需检索优势**: 证明目标导向搜索通过按需检索避免压缩盲点
4. **任务依赖性分析**: 不同任务类型对两种方法的适用性不同
5. **实践建议**: 为不同场景选择记忆策略提供实证指导

## 研究背景与问题

长期记忆研究中，记忆压缩（压缩所有历史为紧凑表示）和目标导向搜索（保持完整历史但按需检索）是两条技术路线。哪种更适合 LLM Agent 的长期记忆？此前缺乏系统性比较。

## 核心方法

1. **Long-Context Memory Benchmark**: 构建包含多种任务的长程记忆基准
2. **Compression Methods**: 实现多种压缩基线（摘要、稀疏编码、记忆增强）
3. **Search Methods**: 实现多种目标导向搜索基线（向量检索、BM25、神经检索）
4. **Ablation Study**: 分析压缩粒度、检索质量对最终性能的影响
5. **Compression Blind Spot Analysis**: 量化分析被压缩信息在后续查询中的价值

## 为什么重要

该论文挑战了"记忆压缩是解决长程记忆问题最佳方案"的常见假设，提供实证证据说明目标导向搜索的优越性。这对 Agent 记忆系统的设计有重要启示：不是先压缩后检索，而是应该保持完整记忆并优化检索。

## 与移动端/端侧相关性

1. **按需检索**: 目标导向搜索只在需要时消耗计算资源，适合资源受限的移动端
2. **无压缩损失**: 不压缩意味着没有信息损失，对精度要求高的移动端任务很重要
3. **可与缓存结合**: 搜索结果可缓存，避免重复计算
4. **移动端搜索优化**: 移动端向量检索已有高效实现（如 FAISS mobile）
