---
title: "MPCS: Neuroplastic Continual Learning via Multi-Component Plasticity and Topology-Aware EWC"
arXiv: 2605.02509
date: 2026-05-04
tags: [agent-memory, continual-learning, catastrophic-forgetting, neuroinspired]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **作者**: Joern Hentsch
- **发表**: 2026-05-04
- **方向**: 持续学习 · 灾难性遗忘 · 神经形态计算

## 摘要（翻译）

持续学习系统面临**可塑性（获取新知识）与稳定性（保留先前知识）**之间的根本张力。本文提出 **MPCS（Multi-Plasticity Continual System）**，一种神经塑性架构，集成了 11 种互补机制：

1. 任务驱动的神经发生（neurogenesis）
2. 傅里叶编码输入
3. EWC 正则化
4. 元回放（meta-replay）
5. 混合整合
6. 混合门控
7. 突触修剪/再生
8. Hebbian 更新
9. 任务相似度路由
10. 自适应增长控制
11. 连续神经元重要性追踪

在 MEP-BENCH 基准上评估——跨越 31 个任务的 Multi-Track 基准，涵盖回归、分类、逻辑和混合领域——使用三维 Pareto 标准（任务性能 Perf、表示多样性 RD、梯度冲突率 GCR）。在 15 种配置（3 seeds × 4 tracks × 2000 epochs）下，MPCS 达到 **94.2 的归一化效率分数**，位于 14 个门控通过系统中的 Pareto 前沿。

## 关键发现

1. **傅里叶编码是最关键的单一部件**：移除后 Perf 下降 30.7 个百分点，且 14% 任务的 MEP 门控失败
2. **全局 EWC 实际上降低性能**（NES = -4.2）；拓扑局部 EWC 可缓解但无法消除该惩罚
3. **完全移除 EWC 产生了最高 Perf 系统 MPCS_EFFICIENT**：建立了单调关系 `全局 EWC < 拓扑 EWC < 无 EWC`（在高任务相似度 regime 下）
4. **Pareto 状态评估具有预测性**：联合移除两个 Pareto 支配组件（EWC + Hebbian）产生 MPCS_EFFICIENT，Perf 提升 0.6 pp，计算成本降低 4.7 倍

## 为什么重要

MPCS 系统性地探索了 11 种互补机制的交互，揭示了：
- 某些组合机制之间存在意外的负向交互（EWC 反而有害）
- Pareto 前沿分析是评估持续学习系统的可行方法
- 神经科学启发的机制（神经发生、Hebbian 更新）为人工持续学习提供了真实有效的设计空间

## 与移动端/端侧的相关性

移动端持续学习的关键挑战是**有限容量下的稳定性-可塑性权衡**：
- 端侧模型需要在不干扰已学能力的情况下适应新任务
- MPCS 的参数高效特性（神经发生只在需要时增长）对移动端资源约束有直接意义
- 拓扑感知 EWC 为移动端个性化适应提供了新思路

---

*注：本文为新发现论文（2605.02509）。*
