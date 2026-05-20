---
title: "Shapley Neuron Values for Continual Learning: Which Neurons Matter Most?"
arXiv: 2605.15877
date: 2026-05-15
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv
---

## 摘要

持续学习使神经网络能够顺序学习任务而不遗忘已有知识。然而，神经网络存在灾难性遗忘问题——学习新任务会降低对早期任务的性能。本文提出 Shapley Neuron Valuation (SNV)，一个基于合作博弈论的原则性框架，用于量化持续学习中神经元的重要性。SNV 选择性地冻结重要神经元，同时保持其他神经元可塑性，实现无需外部 replay buffer 的无缓冲持续学习。在 ImageNet-1k 上的实验表明，SNV 在类增量学习和任务增量学习场景中分别提升准确率 +2.88% 和 +6.46%。

## 核心贡献

1. **Shapley 值框架**：首次将合作博弈论中的 Shapley 值引入持续学习的神经元重要性评估，为每个神经元分配基于其对任务贡献的公平重要性分数
2. **选择性冻结机制**：根据 Shapley 值选择性地冻结重要神经元，保持其他神经元可塑，避免了传统 EWC 等方法的梯度干扰问题
3. **无 buffer 持续学习**：不依赖外部 episodic memory buffer，只使用模型参数本身存储知识，显著降低内存开销
4. **ImageNet-1k 大规模验证**：在类增量（class-incremental）和任务增量（task-incremental）两种场景下均超越现有 buffer-free 方法

## 为什么重要

灾难性遗忘是阻碍神经网络持续学习的关键问题。现有方法要么需要外部记忆（如 replay buffer），要么需要架构扩展（如 PackNet），要么依赖正则化（如 EWC/LwF）。SNV 的创新在于：不增加任何额外内存开销，只通过重新分配参数中重要神经元的"角色"，在保持新任务学习能力的同时保护旧任务知识。这为资源受限的端侧持续学习提供了新思路。

## 实验结果

| 方法 | 准确率 | 遗忘率 |
|------|--------|--------|
| LwF | 72.1% | 10.2% |
| EWC | 74.8% | 8.5% |
| SI | 75.9% | 7.8% |
| SNV (Ours) | **82.36%** | **4.2%** |

## 与移动端/端侧的相关性

SNV 的无 buffer 设计对端侧持续学习有直接价值：在手机、智能手表等内存受限设备上，无需额外存储样本或扩展模型即可实现持续学习。Shapley 值的计算可离线完成，冻结策略可在部署后静态执行，是轻量级端侧持续学习的可行方案。

## 参考文献

Vahedifar, M. A., Ray, A., & Zhang, Q. (2026). Shapley Neuron Values for Continual Learning: Which Neurons Matter Most? arXiv:2605.15877.
