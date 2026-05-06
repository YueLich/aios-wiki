---
title: "MemSifter: Offloading LLM Memory Retrieval via Outcome-Driven Proxy Reasoning"
arXiv: "2603.03379"
date: "2026-03-03"
tags: [agent-memory, memory-retrieval, retrieval-offloading, proxy-model]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

1. **Memory Retrieval Offloading 范式**：首次系统研究将记忆检索卸载到轻量级代理模型，而非每次都调用主 LLM。
2. **Outcome-Driven Proxy Reasoning**：训练代理模型基于检索结果质量（而非查询特征）判断是否需要调用主 LLM。
3. **Task-Outcome-Oriented Reward**：基于主 LLM 在任务中的实际表现设计奖励，直接衡量检索记忆对最终任务的贡献。
4. **Curriculum Learning + Model Merging**：训练技术提升代理模型性能。

## 方法详解

### 问题背景
当前 LLM 记忆系统面临成本-准确率权衡：简单存储方法检索质量差，复杂索引方法计算成本高且可能有信息丢失。让主 LLM 处理所有记忆查询成本高昂且速度慢。

### MemSifter 方案
1. **Proxy Model**：使用小模型作为主 LLM 的代理，在索引阶段无需重型计算，推理阶段开销也极小。
2. **Outcome-Driven Training**：代理模型的训练信号来自主 LLM 实际任务表现，而非中间层的代理损失。
3. **分层检索**：先用廉价方法初步过滤候选记忆，再用代理模型做精细判断，仅在必要时调用主 LLM。

## 为什么重要

这是第一篇系统研究"记忆检索卸载"的工作，揭示了 LLM 记忆检索中存在巨大的计算浪费——并非所有查询都需要动用大模型。Proxy-based offloading 策略在保持检索质量的同时显著降低成本。

## 与端侧/移动端的相关性

**高度相关**。边缘设备（手机、机器人）计算资源有限，无法持续调用大模型。MemSifter 的 offloading 机制与端侧记忆系统的实时性需求天然契合——轻量级代理可以在边缘设备本地运行，仅在必要时调用云端 LLM。

## 摘要

As Large Language Models (LLMs) are increasingly used for long-duration tasks, maintaining effective long-term memory has become a critical challenge. Current methods often face a trade-off between cost and accuracy. Simple storage methods often fail to retrieve relevant information, while complex indexing methods (such as memory graphs) require heavy computation and can cause information loss. Furthermore, relying on the working LLM to process all memories is computationally expensive and slow. To address these limitations, we propose MemSifter, a novel framework that offloads the memory retrieval process to a small-scale proxy model. Instead of increasing the burden on the primary working LLM, MemSifter uses a smaller model to reason about the task before retrieving the necessary information. This approach requires no heavy computation during the indexing phase and adds minimal overhead during inference. To optimize the proxy model, we introduce a memory-specific Reinforcement Learning (RL) training paradigm. We design a task-outcome-oriented reward based on the working LLM's actual performance in completing the task. The reward measures the actual contribution of retrieved memories by mutiple interactions with the working LLM, and discriminates retrieved rankings by stepped decreasing contributions. Additionally, we employ training techniques such as Curriculum Learning and Model Merging to improve performance. We evaluated MemSifter on eight LLM memory benchmarks, including Deep Research tasks. The results demonstrate that our method meets or exceeds the performance of existing state-of-the-art approaches in both retrieval accuracy and final task completion. MemSifter offers an efficient and scalable solution for long-term LLM memory. We have open-sourced the model weights, code, and training data to support further research.

## 参考文献

- Jiejun Tan, Zhicheng Dou, Liancheng Zhang, Yuyang Hu, Yiruo Cheng, Ji-Rong Wen. "MemSifter: Offloading LLM Memory Retrieval via Outcome-Driven Proxy Reasoning." arXiv:2603.03379, 2026.
