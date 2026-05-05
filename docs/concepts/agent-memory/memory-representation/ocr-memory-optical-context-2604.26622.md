---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory

## 论文基本信息

- **作者**: Jinze Li, Yang Zhang, Xin Yang, Jiayi Qu, Jinfeng Xu, +3 more
- **arXiv**: https://arxiv.org/abs/2604.26622
- **领域**: cs.CL
- **备注**: Accepted to ACL 2026 (Main Conference)

## 摘要

Autonomous LLM agents increasingly operate in long-horizon, interactive settings where success depends on reusing experience accumulated over extended histories. However, existing agent memory systems are fundamentally constrained by text-context budgets: storing or revisiting raw trajectories is prohibitively token-expensive, while summarization and text-only retrieval trade token savings for information loss and fragmented evidence. To address this limitation, we propose Optical Context Retrieval Memory (OCR-Memory), a memory framework that leverages the visual modality as a high-density representation of agent experience, enabling retention of arbitrarily long histories with minimal prompt overhead at retrieval time. Specifically, OCR-Memory renders historical trajectories into images annotated with unique visual identifiers. OCR-Memory retrieves stored experience via a \emph{locate-and-transcribe} paradigm that selects relevant regions through visual anchors and retrieves the corresponding verbatim text, avoiding free-form generation and reducing hallucination. Experiments on long-horizon agent benchmarks show consistent gains under strict context limits, demonstrating that optical encoding increases effective memory capacity while preserving faithful evidence recovery.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
