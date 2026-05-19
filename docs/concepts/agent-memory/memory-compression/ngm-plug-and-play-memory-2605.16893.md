---
title: "NGM: A Plug-and-Play Training-Free Memory Module for LLMs"
arXiv: "2605.16893"
date: "2026-05-16"
tags: [agent-memory, memory-compression, plug-and-play, training-free]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

**N-gram Memory (NGM)** 提出了一种无需训练、即插即用的记忆模块，用于增强 LLM 的知识获取能力。核心贡献：

1. **Causal N-Gram Encoder（因果 N-gram 编码器）**：直接对骨干模型预训练的 token 嵌入进行平均来构建 N-gram 表示，无需从头训练独立的 N-gram 嵌入，无需额外的记忆表或检索流水线

2. **Cosine-Gated Memory Injector（余弦门控记忆注入器）**：使用非参数余弦门和 ReLU 将检索到的嵌入调制到上下文表示中

3. **在 Qwen3 系列（0.6B 到 14B）上评估**，涵盖 8 个基准测试，NGM 平均性能提升 0.5-1.2 分，在代码生成和知识密集型任务上提升尤为明显（如 Qwen3-14B 上 LiveCodeBench +3.0，GPQA +3.03），在多模态基准上也有改进（MMStar +1.53 on Qwen3-VL-2B）

## 为什么重要

现有条件记忆模块虽然将知识存储与神经计算解耦，但仍依赖学习到的记忆嵌入，需要额外训练且灵活性受限。NGM 通过纯 N-gram 方法实现了真正的即插即用——无需训练、无需记忆表、无需检索流水线。这是一个很有价值的端侧 AI 方向：可以在不改变模型权重的情况下动态增强 LLM 的知识访问能力。

## 与移动端/端侧相关性

NGM 的即插即用、无需训练特性使其成为端侧部署的理想选择：
- 无需额外训练，适合资源受限的移动/边缘设备
- 无需检索流水线，推理延迟低
- 可作为 LLM 的外挂记忆模块，按需增强特定任务能力

## 参考文献

Yuwen Qu, Wenhui Dong, Chenyang Si, Caifeng Shan. "NGM: A Plug-and-Play Training-Free Memory Module for LLMs." arXiv:2605.16893, 2026.
