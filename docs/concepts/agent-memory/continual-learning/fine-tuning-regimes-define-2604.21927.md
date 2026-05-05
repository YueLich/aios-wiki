---
title: "Fine-Tuning Regimes Define Distinct Continual Learning Problems"
arXiv: 2604.21927
date: 2026-04-23
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Fine-Tuning Regimes Define Distinct Continual Learning Problems

## 论文基本信息

- **作者**: Paul-Tiberiu Iordache, Elena Burceanu
- **arXiv**: https://arxiv.org/abs/2604.21927
- **领域**: cs.LG
- **备注**: 14 pages, 3 figures

## 摘要

Continual learning (CL) studies how models acquire tasks sequentially while retaining previously learned knowledge. Despite substantial progress in benchmarking CL methods, comparative evaluations typically keep the fine-tuning regime fixed. In this paper, we argue that the fine-tuning regime, defined by the trainable parameter subspace, is itself a key evaluation variable. We formalize adaptation regimes as projected optimization over fixed trainable subspaces, showing that changing the trainable depth alters the effective update signal through which both current task fitting and knowledge preservation operate. This analysis motivates the hypothesis that method comparisons need not be invariant across regimes. We test this hypothesis in task incremental CL, five trainable depth regimes, and four standard methods: online EWC, LwF, SI, and GEM. Across five benchmark datasets, namely MNIST, Fashion MNIST, KMNIST, QMNIST, and CIFAR-100, and across 11 task orders per dataset, we find that the relative ranking of methods is not consistently preserved across regimes. We further show that deeper adaptation regimes are associated with larger update magnitudes, higher forgetting, and a stronger relationship between the two. These results show that comparative conclusions in CL can depend strongly on the chosen fine-tuning regime, motivating regime-aware evaluation protocols that treat trainable depth as an explicit experimental factor.

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
