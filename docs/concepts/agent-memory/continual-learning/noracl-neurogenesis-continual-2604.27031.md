---
title: "NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning"
arXiv: 2604.27031
date: 2026-04-30
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# NORACL: Neurogenesis for Oracle-free Resource-Adaptive Continual Learning

**作者:** Karthik Charan Raghunathan, Christian Metzner, Laura Kriener, Melika Payvand
**发表:** 2026-04-30

## 摘要

In a continual learning setting, we require a model to be plastic enough to learn a new task and stable enough to not disturb previously learned capabilities. We argue that this dilemma has an architectural root. A finite network has limited representational and plastic resources, yet the required capacity depends on properties of the future task stream that are unknown: how many tasks will be encountered, and how much they overlap in feature space. Regularization-based methods preserve past knowledge within fixed-capacity architectures and therefore implicitly rely on an oracle architecture sized for this unknown future. When tasks are only weakly related, fixed architectures progressively run out of plastic resources; when tasks are few or strongly overlapping, models are often over-provisioned. Inspired by neurogenesis in biology, we propose NORACL to address the stability-plasticity dilemma by tackling the oracle architecture problem through neuronal growth. Starting from a compact network, NORACL adds neurons adaptively as needed, guided by a validation signal that detects forgetting of prior tasks.

## 核心貢獻

1. **NORACL 框架**: 首个通过神经发生（neurogenesis）解决持续学习稳定性-可塑性困境的方法
2. **Oracle-free 架构适应**: 不依赖对任务流属性的先验知识，通过验证信号检测遗忘并触发神经元增长
3. **自适应神经元增长**: 从紧凑网络出发，根据需要增加神经元，而非预先分配过量容量
4. **遗忘检测信号**: 基于验证集的性能监控，在遗忘发生时指导新神经元添加的位置和数量
5. **生物启发的资源分配**: 借鉴神经生物学中的神经发生机制，动态调整网络容量

## 為什麼重要

持续学习的核心矛盾在于：有限的神经网络必须在「学习新任务」和「保护旧知识」之间取得平衡。NORACL 指出这一困境有架构根源——固定容量网络必然依赖对任务流属性的 oracle 知识。通过神经发生机制，NORACL 从根本上改变了这一前提：网络不再预先分配容量，而是根据实际任务需求动态增长。这为 Agent 记忆系统的长期适应提供了新思路。

## 與端側/移動端相關性

1. **按需增长**: 从最小化网络开始，适合端侧部署的渐进式资源分配
2. **无需任务流先验**: 不依赖对未来的预测，适合开放世界移动 Agent
3. **遗忘检测信号**: 可作为端侧记忆监控指标，决定何时触发记忆扩展
4. **生物启发机制**: 神经发生模型为端侧持续学习提供了低能耗的长期适应范式参考
