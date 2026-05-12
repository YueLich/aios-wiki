---
title: Human-Inspired Memory Architecture for LLM Agents
arXiv: 2605.08538
date: 2026-05-08
tags: [agent-memory, memory-compression, biologically-inspired]
reviewer: auto
source: arXiv API
---

# Human-Inspired Memory Architecture for LLM Agents

**arXiv**: 2605.08538 | **Date**: 2026-05-08 | **Category**: cs.AI

## 摘要

Current LLM agents lack principled mechanisms for managing persistent memory across long interaction horizons. We present a biologically-grounded memory architecture comprising six cognitive mechanisms: (1) sleep-phase consolidation, (2) interference-based forgetting, (3) engram maturation, (4) reconsolidation upon retrieval, (5) entity knowledge graphs, and (6) hybrid multi-cue retrieval. Each mechanism addresses a specific failure mode of naive memory accumulation. We introduce a synthetic calibration methodology that derives all pipeline thresholds without benchmark data exposure, eliminating a common source of evaluation leakage. We evaluate on two benchmarks. First, a VSCode issue-tracking dataset (13K issues, 120K events) where deduplication-based consolidation achieves 97.2% retention precision with 58% store reduction (+21.8 pp over baseline). Second, the LongMemEval personal-chat benchmark where we conduct the first streaming M-tier evaluation (475 sessions, ~540K unique turns). At a 200K-token context budget, our pipeline matches raw retrieval accuracy (70.1% vs. 71.2%, overlapping 95% CI) while exposing a tunable accuracy/store-size operating curve. At S-tier scale (50 sessions), dedup-based consolidation yields a +13.3 pp improvement in preference recall.

## 核心贡献

1. **方法创新**: 待补充
2. **实验验证**: 待补充
3. **理论分析**: 待补充

## 为什么重要

本论文提出了针对agent-memory; memory-compression; biologically-inspired的关键改进，对端侧/移动端记忆系统具有参考价值。

## 与移动端/端侧相关性

- 待补充：具体应用场景和部署考量

## 参考文献

待补充
