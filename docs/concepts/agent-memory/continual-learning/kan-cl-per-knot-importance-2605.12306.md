---
title: "KAN-CL: Per-Knot Importance Regularization for Continual Learning with Kolmogorov-Arnold Networks"
arXiv: "2605.12306"
date: "2026-05-12"
tags: [agent-memory, continual-learning, catastrophic-forgetting, kolmogorov-arnold-networks]
reviewer: auto
source: arXiv API
---

# KAN-CL: Per-Knot Importance Regularization for Continual Learning with Kolmogorov-Arnold Networks

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Minjong Cheon |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.12306 |
| **类别** | cs.LG |
| **标签** | agent-memory, continual-learning, catastrophic-forgetting, kolmogorov-arnold-networks |

## 摘要（翻译）

灾难性遗忘仍是持续学习（CL）的核心障碍：跨任务共享的参数相互干扰，现有正则化方法（如 EWC 和 SI）采用均匀惩罚，无法感知参数服务的输入区域。本文提出 KAN-CL，利用 Kolmogorov-Arnold Networks（KAN）的紧支撑样条参数化，在每节点（per-knot）粒度执行重要性加权锚定。作为卷积骨干网络上 EWC 正则化的分类头，KAN-CL 在 Split-CIFAR-10/5T 和 Split-CIFAR-100/10T 上相比仅头部 KAN 基线分别实现 88% 和 93% 的遗忘减少，同时达到或超越所有基线的准确率。

## 核心贡献

1. **KAN-CL 框架**：首个将 KAN 的样条参数化应用于持续学习的工作，利用其局部支撑特性实现细粒度参数重要性估计
2. **Per-Knot 重要性正则化**：在每节点粒度而非每参数粒度估计重要性，避免均匀惩罚带来的过约束问题
3. **与 EWC 的互补性**：KAN-CL 可作为头部，与骨干网络的 EWC（bbEWC）结合，形成双层防遗忘机制
4. **显著遗忘减少**：在标准基准上实现 88-93% 的遗忘减少，优于统一正则化方法

## 为什么重要

KAN-CL 的核心洞察是：传统持续学习方法将参数重要性视为均匀分布，但 KAN 的局部支撑特性天然地允许识别"哪些节点对哪个输入区域重要"。这一发现对 Agent 记忆系统的启示是：**记忆的重要性不是全局统一的，而是与特定上下文相关的局部属性**。

## 与移动端/端侧的相关性

- KAN 的样条参数化可在边缘设备上高效执行，适合资源受限的持续学习场景
- 细粒度的重要性估计使得在端侧进行选择性记忆巩固（selective memory consolidation）成为可能
- 减少遗忘意味着 Agent 无需频繁重新学习已掌握的能力，降低端侧计算和通信开销

## 参考文献

- Cheon, M. (2026). KAN-CL: Per-Knot Importance Regularization for Continual Learning with Kolmogorov-Arnold Networks. arXiv:2605.12306.
