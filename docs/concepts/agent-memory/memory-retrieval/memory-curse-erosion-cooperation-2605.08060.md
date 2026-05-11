---
title: "The Memory Curse: How Expanded Recall Erodes Cooperative Intent in LLM Agents"
arXiv: 2605.08060
date: 2026-05-08
tags: [agent-memory, memory-retrieval, multi-agent]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

Context window expansion is often treated as a straightforward capability upgrade for LLMs, but this paper discovers a systematic failure mode in multi-agent settings. Across 7 LLMs and 4 games over 500 rounds, expanding accessible history degrades cooperation in 18 of 28 model-game settings — a pattern the authors term **the memory curse**. Lexical analysis of 378,000 reasoning traces associates this breakdown with eroding forward-looking intent rather than rising paranoia. Targeted fine-tuning as a cognitive probe (LoRA adapter) confirms the mechanism.

## 核心贡献

1. **Memory Curse 现象的发现**：首次系统性地证明扩大记忆/上下文窗口会系统性地破坏多智能体合作，而不是简单地提升能力
2. **机制诊断**：通过大规模推理轨迹分析（37.8万条），将记忆诅咒归因于"前瞻性意图的侵蚀"而非偏执/不信任的上升
3. **认知探测**：使用 LoRA 微调作为认知探针，验证了机制解释
4. **跨模型泛化**：在 7 种不同 LLM 上验证，涵盖 GPT、Claude、Llama 等多个家族

## 为什么重要

大多数研究追求更长的上下文窗口和更丰富的记忆，假设"记住更多 = 更好"。本文揭示了一个反直觉的失效模式：在需要合作的多智能体场景中，让 Agent 记住更多历史反而会损害团队绩效。这对记忆系统的设计有根本性的启示——记忆不是越多越好，需要有选择性地抑制某些类型的回忆。

## 与移动端/端侧相关性

端侧多智能体系统（如多机器人协作、分布式边缘计算）同样面临记忆规模与协作质量的权衡。本文提供了一个重要的设计警示：盲目扩展端侧 Agent 的记忆窗口可能反而破坏多智能体协作。Memory Curse 的诊断框架可用于评估端侧记忆系统的最优规模。

## 参考文献

- arXiv: https://arxiv.org/abs/2605.08060
- Authors: Jiayuan Liu, Tianqin Li, Shiyi Du
