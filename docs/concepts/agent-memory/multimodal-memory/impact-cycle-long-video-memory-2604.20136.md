---
title: "IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory"
arXiv: 2604.20136
date: 2026-04-22
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory

## 论文基本信息

- **作者**: Weitong Kong, Di Wen, Kunyu Peng, David Schneider, Zeyun Zhong, +8 more
- **arXiv**: https://arxiv.org/abs/2604.20136
- **领域**: cs.CV
- **备注**: 7 pages, 2 figures, code are available at https://github.com/MKong17/IMPACT_CYCLE

## 摘要

Correcting errors in long-video understanding is disproportionately costly: existing multimodal pipelines produce opaque, end-to-end outputs that expose no intermediate state for inspection, forcing annotators to revisit raw video and reconstruct temporal logic from scratch. The core bottleneck is not generation quality alone, but the absence of a supervisory interface through which human effort can be proportional to the scope of each error. We present IMPACT-CYCLE, a supervisory multi-agent system that reformulates long-video understanding as iterative claim-level maintenance of a shared semantic memory -- a structured, versioned state encoding typed claims, a claim dependency graph, and a provenance log. Role-specialized agents operating under explicit authority contracts decompose verification into local object-relation correctness, cross-temporal consistency, and global semantic coherence, with corrections confined to structurally dependent claims. When automated evidence is insufficient, the system escalates to human arbitration as the supervisory authority with final override rights; dependency-closure re-verification then ensures correction cost remains proportional to error scope. Experiments on VidOR show substantially improved downstream reasoning (VQA: 0.71 to 0.79) and a 4.8x reduction in human arbitration cost, with workload significantly lower than manual annotation. Code will be released at https://github.com/MKong17/IMPACT_CYCLE.

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
