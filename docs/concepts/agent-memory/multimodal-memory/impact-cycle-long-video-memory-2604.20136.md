---
title: IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory
arXiv: 2604.20136
date: 2026-04-22
tags: [agent-memory, multimodal_memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **arXiv**: 2604.20136
- **作者**: Weitong Kong, Di Wen, Kunyu Peng, David Schneider, Zeyun Zhong
- **提交日期**: 2026-04-22

## 摘要

Correcting errors in long-video understanding is disproportionately costly: existing multimodal pipelines produce opaque, end-to-end outputs that expose no intermediate state for inspection, forcing annotators to revisit raw video and reconstruct temporal logic from scratch. The core bottleneck is not generation quality alone, but the absence of a supervisory interface through which human effort can be proportional to the scope of each error.

We present IMPACT-CYCLE, a supervisory multi-agent system that reformulates long-video understanding as iterative claim-level maintenance of a shared semantic memory. The system decomposes video content into atomic claims stored in a structured memory, enabling targeted correction without full reprocessing.

A key innovation is the contract-based architecture where multiple agents negotiate claim validity through structured protocols. When an error is detected, the system can trace it to specific claims in memory, correcting only affected entries rather than regenerating entire video summaries. This dramatically reduces annotation cost and enables human supervisors to focus effort proportional to error scope.

Experiments on long-video benchmarks demonstrate that IMPACT-CYCLE reduces correction cost by 60% while improving temporal consistency of semantic memory compared to end-to-end baselines.

## 核心贡献

1. **问题定义**: IMPACT-CYCLE 针对 multimodal memory 领域的关键挑战
2. **方法创新**: 提出了针对该问题的系统性解决方案
3. **实验验证**: 在相关基准上验证了方法的有效性

## 为什么重要

这篇论文在 multimodal、memory 方向上具有重要意义，为该领域提供了新的研究方向和技术路径。

## 与端侧/移动端的相关性

论文中涉及的技术和方法对移动端/端侧部署具有参考价值，特别是在资源受限环境下的记忆系统设计方面。
