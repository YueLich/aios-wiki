---
title: "MPCS: Neuroplastic Continual Learning via Multi-Component Plasticity and Topology-Aware EWC"
arXiv: 2605.02509
date: 2026-05-04
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# MPCS: Neuroplastic Continual Learning via Multi-Component Plasticity and Topology-Aware EWC

## 论文基本信息

- **作者**: Joern Hentsch
- **arXiv**: https://arxiv.org/abs/2605.02509
- **领域**: cs.LG


## 摘要

Continual learning systems face a fundamental tension between plasticity -- acquiring new knowledge  --  and stability  --  retaining prior knowledge. We introduce MPCS (Multi-Plasticity Continual System), a neuroplastic architecture that integrates eleven complementary mechanisms: task-driven neurogenesis, Fourier-encoded inputs, EWC regularization, meta-replay, mixed consolidation, hybrid gating, synapse pruning/regeneration, Hebbian updates, task similarity routing, adaptive growth control, and continuous neuron importance tracking. We evaluate MPCS on MEP-BENCH, a multi-track benchmark spanning 31 tasks across regression, classification, logic, and mixed domains, using a three-dimensional Pareto criterion over task performance (Perf), representation diversity (RD), and gradient conflict rate (GCR). Across 15 ablation configurations (3 seeds x 4 tracks x 2000 epochs), MPCS achieves a Normalized Efficiency Score of 94.2, placing it on the Pareto frontier among 9 of 14 gate-passing systems. Key findings: (i) Fourier encoding is the single most critical component (removal drops Perf by 30.7 pp and fails the MEP gate on 14% of tasks); (ii) global EWC degrades performance (NES = -4.2); topology-local EWC reduces this penalty (NES 90.5-&gt;91.8) but does not eliminate it; removing EWC entirely yields MPCS_EFFICIENT, the highest-Perf system -- establishing a monotone relationship in the high task-similarity regime (s_bar ~= 0.95): global EWC &lt; topology EWC &lt; no EWC; (iii) the Pareto status assessment is predictive: removing the two Pareto-dominated components (EWC + Hebbian) jointly yields MPCS_EFFICIENT, which improves Perf by 0.6 pp at 4.7x lower compute cost (127 vs. 602 min), validating the Pareto frontier as an actionable model-compression guide.

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
