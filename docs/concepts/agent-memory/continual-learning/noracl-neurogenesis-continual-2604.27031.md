---
title: "NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning"
arXiv: 2604.27031
date: 2026-04-29
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning

## 论文基本信息

- **作者**: Karthik Charan Raghunathan, Christian Metzner, Laura Kriener, Melika Payvand
- **arXiv**: https://arxiv.org/abs/2604.27031
- **领域**: cs.LG
- **备注**: 23 pages, 6 figures and 3 tables

## 摘要

In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space. Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture sized for this unknown future. When tasks are only weakly related, fixed architectures progressively run out of plastic resources; when tasks are few or strongly overlapping, models are often over-provisioned. Inspired by neurogenesis in biology, we propose NORACL to address the stability-plasticity dilemma by tackling the oracle architecture problem through neuronal growth. Starting from a compact network, NORACL grows only when needed by monitoring two complementary signals for representational and plasticity saturation. We evaluate NORACL against oracle-sized static baselines across varying task counts and geometries. Across all settings, NORACL achieves final average accuracies that are better than or on par with oracle-provisioned static baselines while using fewer parameters. Additionally, NORACL yields architectures with interpretable growth, i.e. dissimilar tasks predominantly expand feature-extraction layers, whereas tasks which rely on common features shift growth toward later feature-combination layers. Our analysis further explains why fixed-capacity networks lose plasticity as tasks accumulate, whereas NORACL creates fresh capacity for new tasks through growth. Together, these results show that adaptive neurogenesis pushes the stability-plasticity Pareto frontier of continual learning.

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
