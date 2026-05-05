---
title: "Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks"
arXiv: 2604.24637
date: 2026-04-27
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks

## 论文基本信息

- **作者**: Kevin McKee, Thomas Hazy, Yicong Zheng, Zacharie Bugaud, Thomas Miconi
- **arXiv**: https://arxiv.org/abs/2604.24637
- **领域**: cs.LG
- **备注**: 16 pages, 15 figures

## 摘要

Block-sequential continual learning demands that a single model both protect prior solutions from catastrophic forgetting and efficiently infer at inference time which prior solution matches the current input without task labels. We present Functional Task Networks (FTN), a parameter-isolation method inspired by structural and dynamical motifs found in the mammalian neocortex. Similar to mixture-of-experts, this method uses a high dimensional, self-organizing binary mask over a large population of small but deep networks, inspired by dendritic models of pyramidal neurons. The mask is produced by a three-stage procedure: (1) gradient descent on a continuous mask identifies task-relevant neurons, (2) a smoothing kernel biases the result toward spatial contiguity, (3) and k-winner-take-all binarizes the resulting group at a fixed capacity budget. Like mixture-of-experts, each neuron is an independent deep network, so disjoint masks give exactly disjoint gradient updates, providing structural guarantees against catastrophic forgetting. This three-stage procedure recovers the sub-network of a previously-trained task in a single gradient step, providing unsupervised task segmentation at inference time. We test it on three continual-learning benchmarks: (1) a synthetic multi-task classification/regression generator, (2) MNIST with shuffled class labels (pure concept shift), and (3) Permuted MNIST (domain shift). On all three, FTN with fine grained smoothing (FTN-Slow) results in nearly zero forgetting. FTN with a large kernel and only 2 iterations of smoothing (FTN-Fast) trades off some retention for increased speed. We show that the spatial organization mechanism reduces the effective mask search from the combinatorial top-k subset problem in O(C(H,K)) to the complexity of a near-linear scan in O(H) over compact cortical neighborhoods, which is parallelized by the gradient-based update.

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
