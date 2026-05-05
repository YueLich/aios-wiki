---
title: "Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks"
arXiv: 2604.24637
date: 2026-04-27
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Cortex-Inspired Continual Learning: Unsupervised Instantiation and Recovery of Functional Task Networks

**作者:** Kevin McKee, Thomas Hazy, Yicong Zheng, Zacharie Bugaud, Thomas Miconi
**发表:** 2026-04-27

## 摘要

Block-sequential continual learning demands that a single model both protect prior solutions from catastrophic forgetting and efficiently infer at inference time which prior solution matches the current input without task labels. We present Functional Task Networks (FTN), a parameter-isolation method inspired by structural and dynamical motifs found in the mammalian neocortex. Similar to mixture-of-experts, this method uses a high dimensional, self-organizing binary mask over a large population of small but deep networks, inspired by dendritic models of pyramidal neurons. The mask is produced by a three-stage procedure: (1) gradient descent on a continuous mask identifies task-relevant neurons, (2) a smoothing kernel biases the result toward spatial contiguity, (3) and k-winner-take-all binarizes the resulting group at a fixed capacity budget. Like mixture-of-experts, each neuron is an independent deep network, so disjoint masks give exactly disjoint gradient updates, providing structured regularization against catastrophic forgetting. At inference, a simple autoassociative dynamics recovers the correct task identity in a single evaluation, without external task labels.

## 核心貢獻

1. **FTN (Functional Task Networks)**: 首个完全自组织的参数隔离持续学习方法，受哺乳动物新皮层结构与动力学 motif 启发
2. **三层掩码生成机制**: 梯度下降识别 → 空间连续性平滑 → k-winner-take-all 二值化，确保任务专用神经元在空间上连续分布
3. **Autoassociative Task Identity Recovery**: 推理时无需外部任务标签，通过自联想动力学在单次前向传播中恢复正确的任务身份
4. **Disjoint Gradient Updates**: 每个 FTN 神经元是独立深度网络， disjoint masks 保证完全不干扰先前任务梯度
5. **无任务标签的 task identity 推断**: 解决了持续学习中的 "task label-free inference" 难题

## 為什麼重要

持续学习面临两个核心挑战：保护旧任务免受灾难性遗忘，以及在推理时无需任务标签即可识别当前输入对应的任务。FTN 通过借鉴皮层中锥体神经元的树突模型和混合专家机制，同时解决了这两个问题。三阶段掩码机制确保任务专用神经元在空间上连续分布，而 autoassociative dynamics 使模型能在推理时自举恢复任务身份。这对端侧 Agent 的持续适应能力有直接意义。

## 與端側/移動端相關性

1. **参数隔离架构**: 每个任务有独立神经元子集，适合端侧静态部署——任务切换无需重新配置
2. **单次前向推理识别任务**: 低延迟任务身份恢复，适合实时移动应用
3. **固定容量预算**: k-winner-take-all 保证内存消耗有上限，适合资源受限设备
4. **无需外部任务标签**: 降低了对元学习或额外分类器的依赖，简化端侧部署

## 關鍵文獻

- Functional Task Networks (FTN)
- Mixture of Experts (MoE)
- k-Winner-Take-All (k-WTA)
- 哺乳动物新皮层树突模型
