---
title: "MELODI: Exploring Memory Compression for Long Contexts"
arXiv: 2410.03156
date: 2024-10-04
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# MELODI: Exploring Memory Compression for Long Contexts

## 论文基本信息

- **作者**: Yinpeng Chen, DeLesley Hutchins, Aren Jansen, Andrey Zhmoginov, David Racz, Jesper Andersen
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2410.03156
- **代码**: （待补充）

## 核心贡献

1. **层次压缩记忆架构**: 提出 MELODI，一种新颖的记忆架构，在网络层和上下文窗口之间将短期和长期记忆表示为层次压缩方案。
2. **短期记忆**: 通过跨多层对上下文窗口进行循环压缩，实现窗口间平滑过渡。
3. **长期记忆**: 在单层中进行进一步压缩，聚合跨上下文窗口的信息，有效整合整个历史中的关键信息。
4. **8倍内存减少**: 在多种长上下文数据集上表现优于强基线，同时将内存占用减少 8 倍。

## 研究背景与问题

处理长文档需要大量上下文窗口，但现有方法面临内存瓶颈。Memorizing Transformer 使用对大型长期记忆（64K 键值对）的密集注意力，仍存在效率问题。

## 核心方法

**MELODI 层次压缩方案**：

### 短期记忆
- 跨网络多层对上下文窗口进行循环压缩
- 确保窗口之间的平滑过渡

### 长期记忆
- 在单个中间层进行进一步压缩
- 聚合跨上下文窗口的信息
- 有效整合整个历史的关键信息

## 实验结果

- 在多种长上下文数据集上优于强基线
- **内存占用减少 8 倍**（相比 Memorizing Transformer 的 64K KV 记忆）

## 为什么重要

MELODI 的层次压缩思想——区分短期和长期记忆、用不同压缩粒度处理——对 Agent 记忆系统设计有重要启发。这是记忆压缩领域的经典工作，8 倍内存减少的效率提升在实际部署中非常有价值。

## 与移动端/端侧相关性

端侧设备处理长对话/长文档时内存受限严重。MELODI 的层次压缩方案可以在保持关键信息的同时大幅减少记忆占用，对手机端侧 LLM 的长上下文处理有参考意义。
