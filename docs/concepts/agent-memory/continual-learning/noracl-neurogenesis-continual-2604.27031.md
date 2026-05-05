---
title: "NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning"
arXiv: 2604.27031
date: 2026-04-29
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning

**作者:** Karthik Charan Raghunathan, Christian Metzner, Laura Kriener, Melika Payvand  
**发表:** 2026-04-29

## 摘要

In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space. Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture sized for this unknown future. When tasks are only weakly related, fixed architectures progressively run out of plastic resources; when tasks are few or strongly overlapping, models are often over-provisioned. Inspired by neurogenesis in biology, we propose NORACL to address the stability-plasticity dilemma by tackling the oracle architecture problem through neuronal growth. Starting from a compact network, NORACL grows only when needed by monitoring two complementary signals for representational and plasticity saturation. We evaluate NORACL against oracle-sized static baselines across varying task counts and geometries. Across all settings, NORACL achieves final average accuracies that are better than or on par with oracle-provisioned static baselines while using fewer parameters. Additionally, NORACL yields architectures with interpretable growth, i.e. dissimilar tasks predominantly expand feature-extraction layers, whereas tasks which rely on common features shift growth toward later feature-combination layers. Our analysis further explains why fixed-capacity networks lose plasticity as tasks accumulate, whereas NORACL creates fresh capacity for new tasks through growth. Together, these results show that adaptive neurogenesis pushes the stability-plasticity Pareto frontier of continual learning.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
