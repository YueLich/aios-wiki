---
title: "Learning to Forget: Continual Learning with Adaptive Weight Decay"
arXiv: 2604.27063
date: 2026-04-29
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Learning to Forget: Continual Learning with Adaptive Weight Decay

## 论文基本信息

- **作者**: Aditya A. Ramesh, Alex Lewandowski, Jürgen Schmidhuber
- **arXiv**: https://arxiv.org/abs/2604.27063
- **领域**: cs.LG
- **备注**: Preprint version

## 摘要

Continual learning agents with finite capacity must balance acquiring new knowledge with retaining the old. This requires controlled forgetting of knowledge that is no longer needed, freeing up capacity to learn. Weight decay, viewed as a mechanism for forgetting, can serve this role by gradually discarding information stored in the weights. However, a fixed scalar weight decay drives this forgetting uniformly over time and uniformly across all parameters, even when some encode stable knowledge while others track rapidly changing targets. We introduce Forgetting through Adaptive Decay (FADE), which adapts per-parameter weight decay rates online via approximate meta-gradient descent. We derive FADE for the online linear setting and apply it to the final layer of neural networks. Our empirical analysis shows that FADE automatically discovers distinct decay rates for different parameters, complements step-size adaptation, and consistently improves over fixed weight decay across online tracking and streaming classification problems.

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
