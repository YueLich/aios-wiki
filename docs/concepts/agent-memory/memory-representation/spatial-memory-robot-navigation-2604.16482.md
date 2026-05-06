---
title: "A Survey of Spatial Memory Representations for Efficient Robot Navigation"
arXiv: 2604.16482
date: 2026-04-13
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# A Survey of Spatial Memory Representations for Efficient Robot Navigation

## 论文基本信息

- **作者**: Mohan Guo, et al.
- **arXiv**: https://arxiv.org/abs/2604.16482
- **领域**: cs.RO, cs.CV

## 摘要

随着视觉机器人导航的环境规模增大，空间记忆无限增长，最终耗尽计算资源——尤其在嵌入式平台（8-16GB 共享内存，<30W）上，无法通过添加硬件解决。该调研审查了 88 篇参考文献，覆盖 52 个系统（1989-2025），从占用栅格到神经隐式表示。论文引入 α = M_peak / M_map（运行时峰值内存与持久化地图大小的比值），揭示发表地图大小与实际部署成本之间的差距。在 NVIDIA A100 GPU 上独立分析显示，α 在神经方法内跨越两个数量级（2.3 到 215）。论文提出标准化评估协议，包括内存增长率、查询延迟、内存完整性曲线和吞吐量衰减。

## 核心贡献

1. **Spatial Memory Efficiency Survey**: 首个系统性调研机器人导航空间记忆效率的研究
2. **α Metric**: 引入峰值内存 / 地图大小比值，揭示发表指标与实际部署成本的差距
3. **α-aware Budgeting Algorithm**: 提出考虑 α 的内存预算算法
4. **Pareto Frontier Analysis**: 展示不同范式在各自评估 regime 内的主导关系
5. **标准化协议**: 内存增长率、查询延迟、内存完整性曲线、吞吐量衰减

## 研究背景与问题

现有调研评估通常只关注地图大小（存储），忽视运行时峰值内存。神经方法尤其如此——小地图可能需要巨大的运行时内存（α = 215 意味着 47MB 地图在运行时需要 10GB）。

## 核心方法

1. **Independent Profiling**: 在 NVIDIA A100 上独立测试各方法的实际内存消耗
2. **α Taxonomy**: 系统分类不同空间记忆表示的 α 值分布
3. **Pareto Analysis**: 在准确率 vs 内存效率的 Pareto 前沿上分析各方法
4. **Deployment Feasibility Assessment**: 帮助从业者在实施前评估目标硬件上的可行性

## 为什么重要

这是首个系统揭示空间记忆"发表指标"与"实际部署成本"差距的研究。对需要在嵌入式/移动端部署导航 Agent 的系统，必须关注 α 而非仅地图大小。

## 与移动端/端侧相关性

1. **嵌入式平台约束**: 8-16GB 共享内存、<30W 功耗是移动机器人的典型约束
2. **α-aware 设计**: 端侧导航系统设计必须考虑 α 值
3. **资源预算算法**: 论文提出的预算算法可直接应用于端侧内存管理
4. **感知 vs 记忆权衡**: 调研揭示了感知精度与记忆效率之间的权衡
