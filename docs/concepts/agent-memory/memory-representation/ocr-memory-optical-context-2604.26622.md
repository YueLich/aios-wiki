---
title: OCR-Memory: Optical Context Retrieval for Long-Horon Agent Memory
arXiv: 2604.26622
date: 2026-04-29
tags: [agent-memory, memory_representation]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.26622
- **作者**: Jinze Li, Yang Zhang, Xin Yang, Jiayi Qu, Jinfeng Xu
- **提交日期**: 2026-04-29

## 摘要

Autonomous LLM agents increasingly operate in long-horizon, interactive settings where success depends on reusing experience accumulated over extended histories. However, existing agent memory systems are fundamentally constrained by text-context budgets: storing or revisiting raw trajectories is prohibitively token-expensive, while summarization and text-only retrieval trade token savings for information loss and fragmented evidence.

To address this limitation, we propose Optical Context Retrieval Memory (OCR-Memory), a memory framework that leverages the visual modality as a high-density representation of agent experience, enabling retention of arbitrarily long histories with minimal prompt overhead at retrieval time.

Specifically, OCR-Memory renders historical trajectories into images annotated with unique visual identifiers. OCR-Memory retrieves stored experience via a locate-and-transcribe paradigm that selects relevant regions through visual anchors and retrieves the corresponding verbatim text, avoiding free-form generation and reducing hallucination.

Experiments on long-horizon agent benchmarks show consistent gains under strict context limits, demonstrating that optical encoding increases effective memory capacity while preserving faithful evidence recovery.

## 核心贡献

1. **问题定义**: OCR-Memory 针对 memory representation 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 memory、representation 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
