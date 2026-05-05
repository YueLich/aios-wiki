---
title: "PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning"
arXiv: 2605.01061
date: 2026-05-01
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning

## 论文基本信息

- **作者**: Beining Wu, Zihao Ding, Jun Huang
- **arXiv**: https://arxiv.org/abs/2605.01061
- **领域**: cs.MM
- **备注**: submitted to IEEE

## 摘要

While current federated multimodal continual learning over mixture-of-experts low-rank adaptation (MoE-LoRA) is built on the unverified assumption that routing isolates task-specific knowledge into disjoint experts, we argue that routing operates per-sample, while forgetting accumulates across the task sequence, and gradient conflict persists within each expert even when routing is maximally polarized. Moreover, activation-subspace protection can also fail because, under parameter-efficient fine-tuning, it entangles tasks due to a dimension-counting bound, and federated averaging (FedAvg) disrupts client-side orthogonality. To address this, we propose PRISM (Per-expert Routing-projection Interference-informed Subspace Method), which maintains a per-expert gradient subspace basis whose orthogonality is preserved under FedAvg and reinterprets MoE routing as a capacity allocator. Our results show that, on LLaVA-1.5-7B, LLaVA-1.5-13B, and Qwen2.5-VL-7B across CoIN-6 and CoIN-Long-10, PRISM outperforms sixteen the state of the art baselines in average accuracy. Compared to the best federated multimodal baseline, the performance margin increases from +3.23 pp on CoIN-6 to +6.06 pp on CoIN-Long-10.

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
