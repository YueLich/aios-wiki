---
title: "Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks"
arXiv: 2604.24637
date: 2026-04-27
tags: [continual-learning, cortex-inspired, functional-task-networks, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

# Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks

## 论文基本信息

- **arXiv ID**: 2604.24637
- **作者**: (From paper)
- **提交日期**: 2026-04-27
- **类别**: cs.LG, cs.AI, cs.NE

## 摘要

Block-sequential continual learning demands that a single model both protect prior solutions from catastrophic forgetting and efficiently infer at inference time which prior solution matches the current input without task labels. We present Functional Task Networks (FTN), a parameter-isolation method inspired by structural and dynamical motifs found in the mammalian neocortex. Similar to mixture-of-experts, this method uses a high-dimensional, self-organizing binary mask over a large population of small but deep networks, inspired by dendritic models of pyramidal neurons. The mask is produced by a three-stage procedure: (1) gradient下降 on a continuous mask identifies task-relevant neurons, (2) a smoothing kernel biases the result toward spatial contiguity, (3) and k-winner-take-all binarizes the resulting group at a fixed capacity budget. Each neuron is an independent deep network, so disjoint masks give exactly disjoint gradient updates, providing structural guarantees against catastrophic forgetting. This three-stage procedure recovers the sub-network of a previously-trained task in a single gradient step, providing unsupervised task segmentation at inference time. On MNIST shuffled labels, Permuted MNIST, and multi-task classification/regression, FTN-Slow results in nearly zero forgetting.

## 核心贡献

1. **皮层启发式参数隔离**：受哺乳动物新皮层结构和动力学 motif 启发的功能任务网络。
2. **三阶段掩码程序**：梯度下降识别任务相关神经元 → 平滑核偏向空间连续性 → k-winner-take-all 二值化。
3. **结构保证防止遗忘**：每个神经元是独立深度网络，不相交掩码产生不相交梯度更新。
4. **单步恢复机制**：推理时单梯度步恢复先前训练任务的子网络，实现无监督任务分割。

## 为什么重要

FTN 通过生物学启发的架构在持续学习的所有测试基准上几乎实现零遗忘。三阶段掩码程序将任务相关神经元的识别、空间连续性约束和容量预算管理统一起来。最重要的是，不相交掩码提供了防止灾难性遗忘的结构性保证——这是持续学习领域的重要理论进展。

## 与移动端/端侧相关性

- 零遗忘保证对移动端多任务学习非常重要——用户不希望新功能学习破坏已有能力
- 单步恢复机制计算高效，适合移动端实时推理场景
- 无监督任务分割无需显式任务边界标注，减少端侧标注成本
- 与 MoE 架构的协同可能为端侧多专家模型提供新的持续学习路径
