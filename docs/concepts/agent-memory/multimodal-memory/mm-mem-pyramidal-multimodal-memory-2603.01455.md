---
title: "From Verbatim to Gist: Distilling Pyramidal Multimodal Memory via Semantic Information Bottleneck for Long-Horizon Video Agents"
arXiv: 2603.01455
date: 2026-03-02
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# From Verbatim to Gist: Distilling Pyramidal Multimodal Memory via Semantic Information Bottleneck for Long-Horizon Video Agents

## 论文基本信息

- **作者**: Niu Lian, Yuting Wang, Hanshu Yao, Jinpeng Wang, Bin Chen, +3 more
- **arXiv**: https://arxiv.org/abs/2603.01455
- **领域**: cs.CV
- **备注**: Accepted by ACL 2026 Main. 17 pages, 7 figures, 8 tables. TL;DR: We propose MM-Mem, a cognition-inspired, dual-trace hierarchical memory framework for long-horizon video understanding grounded in Fuzzy-Trace Theory. It features adaptive memory compression via the Information Bottleneck and employs an entropy-driven top-down retrieval to access fine-grained details only when necessary

## 摘要

While multimodal large language models have demonstrated impressive short-term reasoning, they struggle with long-horizon video understanding due to limited context windows and static memory mechanisms that fail to mirror human cognitive efficiency. Existing paradigms typically fall into two extremes: vision-centric methods that incur high latency and redundancy through dense visual accumulation, or text-centric approaches that suffer from detail loss and hallucination via aggressive captioning. To bridge this gap, we propose MM-Mem, a pyramidal multimodal memory architecture grounded in Fuzzy-Trace Theory. MM-Mem structures memory hierarchically into a Sensory Buffer, Episodic Stream, and Symbolic Schema, enabling the progressive distillation of fine-grained perceptual traces (verbatim) into high-level semantic schemas (gist). Furthermore, to govern the dynamic construction of memory, we derive a Semantic Information Bottleneck objective and introduce SIB-GRPO to optimize the trade-off between memory compression and task-relevant information retention. In inference, we design an entropy-driven top-down memory retrieval strategy. Extensive experiments across 4 benchmarks confirm that MM-Mem achieves state-of-the-art performance on both offline and streaming tasks, demonstrating robust generalization and validating the effectiveness of cognition-inspired memory organization. Code and associated configurations are publicly available at https://github.com/EliSpectre/MM-Mem.

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
