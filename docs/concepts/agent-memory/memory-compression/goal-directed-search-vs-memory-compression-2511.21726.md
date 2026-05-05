---
title: "Goal-Directed Search Outperforms Goal-Agnostic Memory Compression in Long-Context Memory Tasks"
arXiv: 2511.21726
date: 2025-11-20
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Goal-Directed Search Outperforms Goal-Agnostic Memory Compression in Long-Context Memory Tasks

**作者:** Yicong Zheng, Kevin L. McKee, Thomas Miconi, Zacharie Bugaud, Mick van Gelderen et al.  
**发表:** 2025-11-20

## 摘要

How to enable human-like long-term memory in large language models (LLMs) has been a central question for unlocking more general capabilities such as few-shot generalization. Existing memory frameworks and benchmarks focus on finding the optimal memory compression algorithm for higher performance in tasks that require recollection and sometimes further reasoning. However, such efforts have ended up building more human bias into the compression algorithm, through the search for the best prompts and memory architectures that suit specific benchmarks, rather than finding a general solution that would work on other data distributions. On the other hand, goal-directed search on uncompressed information could potentially exhibit superior performance because compression is lossy, and a predefined compression algorithm will not fit all raw data distributions. Here we present SUMER (Search in Uncompressed Memory via Experience Replay), an end-to-end reinforcement learning agent with verifiable reward (RLVR) that learns to use search tools to gather information and answer a target question. On the LoCoMo dataset for long-context conversation understanding, SUMER with Qwen2.5-7B-Instruct learned to use search tools and outperformed all other biased memory compression approaches and also the full-context baseline, reaching SOTA performance (43% gain over the prior best). We demonstrate that a simple search method applied to raw data outperforms goal-agnostic and biased compression algorithms in current long-context memory tasks, arguing for new paradigms and benchmarks that are more dynamic and autonomously scalable. Code for SUMER and all implemented baselines is publicly available at https://github.com/zycyc/SUMER.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
