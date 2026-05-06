---
title: "MemSifter: Offloading LLM Memory Retrieval via Outcome-Driven Proxy Reasoning"
arXiv: "2603.03379"
date: "2026-03-03"
tags: [agent-memory, memory-retrieval, retrieval-offloading]
reviewer: auto
source: arXiv RSS
---

## 核心贡献

MemSifter 针对 LLM 记忆检索中的成本-准确率权衡问题，提出将记忆检索卸载（offload）到轻量级代理的框架。

**核心问题**：现有方法在记忆检索中面临两难——
- 简单存储方法（naive storage）检索准确率低
- 复杂索引方法（如记忆图谱）计算开销大
- 依赖 LLM 处理所有记忆成本高且速度慢

**MemSifter 方案**：
1. **Outcome-Driven Proxy Reasoning**：训练一个轻量级代理（proxy），基于查询结果的质量信号来判断是否需要动用主 LLM
2. **分层检索架构**：先用廉价方法初步过滤，再用 LLM 做精细判断
3. **结果驱动的卸载策略**：根据代理推理的outcome（而非 query 特征）决定是否调用 LLM

## 为什么重要

这是第一篇系统研究"记忆检索卸载"的工作，揭示了 LLM 记忆检索中存在巨大的计算浪费——并非所有查询都需要动用大模型。Proxy-based offloading 策略在保持检索质量的同时显著降低成本。

## 与端侧/移动端的相关性

**高度相关**。边缘设备（手机、机器人）计算资源有限，无法持续调用大模型。MemSifter 的 offloading 机制与端侧记忆系统的实时性需求天然契合——轻量级代理可以在边缘设备本地运行，仅在必要时调用云端 LLM。

## 摘要

As Large Language Models (LLMs) are increasingly used for long-duration tasks, maintaining effective long-term memory has become a critical challenge. Current methods often face a trade-off between cost and accuracy. Simple storage methods often fail to retrieve relevant information, while complex indexing methods (such as memory graphs) require heavy computation and can cause information loss. Furthermore, relying on the working LLM to process all memories is computationally expensive and slow. To address these limitations, we propose MemSifter, a novel framework that offloads the memory retrieval to a lightweight proxy.

## 参考文献

待补充
