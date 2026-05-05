---
title: "Clustering-driven Memory Compression for On-device Large Language Models"
arXiv: 2601.17443
date: 2026-01-24
tags: [agent-memory, memory-compression, on-device]
reviewer: auto
source: arXiv RSS/API
---

# Clustering-driven Memory Compression for On-device Large Language Models

## 论文基本信息

- **作者**: Ondrej Bohdal, Pramit Saha, Umberto Michieli, Mete Ozay, Taha Ceritli
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2601.17443
- **代码**: （待补充）

## 核心贡献

1. **聚类驱动的记忆压缩策略**: 提出基于聚类的记忆压缩策略，在上下文效率和个性化质量之间取得平衡。
2. **按相似性分组 + 组内合并**: 将记忆按相似性分组，在组内合并后再拼接，保持连贯性同时减少冗余。
3. **显著降低记忆 token 数量**: 显著减少记忆 token 数量的同时优于基线策略。

## 研究背景与问题

LLM 通常依赖从过去交互中提炼的用户特定记忆来实现个性化生成。常见做法是将这些记忆与输入 prompt 拼接，但：

- **上下文消耗大**: 对于上下文窗口有限的端侧 LLM，这种方式很快耗尽可用上下文
- **平均压缩的缺陷**: 通过平均压缩记忆可以缓解上下文增长，但因语义冲突通常损害性能

## 核心方法

**聚类驱动的记忆压缩**：

1. **相似性分组**: 将记忆按语义相似性分组
2. **组内合并**: 在组内对记忆进行合并（averaging within clusters）
3. **合并后拼接**: 将合并后的记忆与输入拼接

**优势**：
- 保留语义连贯性（因为冲突的记忆被分组合并了）
- 减少冗余（重复信息在组内被合并）
- 减少 token 数量

## 实验结果

实验表明：
- 记忆 token 数量大幅降低
- 优于朴素平均或直接拼接等基线策略
- 在固定上下文预算下，压缩后的记忆表示更紧凑，生成质量更高

## 为什么重要

这篇论文直接针对端侧 LLM 的记忆瓶颈问题，提出了一个简单而有效的解决方案——聚类合并。对移动端/手表等内存受限设备的个性化 Agent 系统有直接应用价值。

## 与移动端/端侧相关性

**高度相关**。这是专门针对端侧 LLM 的记忆压缩工作，关键词包括 on-device。对于手机、智能手表等资源受限设备上的个性化记忆系统，聚类驱动压缩可以在保持个性化质量的同时适应严格的上下文限制。
