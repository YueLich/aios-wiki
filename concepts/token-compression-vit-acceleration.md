---
type: concept
tags: [vision-transformer, token-compression, edge-vision, 3d-detection, inference-acceleration, 视觉加速]
related: [[multimodal-edge-pruning]], [[compressed-sensing-dynamic-reduction]], [[sense-less-infer-more]], [[dancemoe-distributed-moe-edge]], [[cora-mobile-gui-safety]]
sources:
  - url: https://arxiv.org/abs/2604.14563
    title: "Revisiting Token Compression for Accelerating ViT-based Sparse Multi-View 3D Object Detectors"
    date: 2026-04-19
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Token Compression for ViT: 重新审视视觉 Transformer 的 Token 压缩策略

> 系统重新审视 ViT 稀疏多视角 3D 检测器的 token 压缩策略，发现现有方法（剪枝+合并）存在精度-速度权衡的盲区，提出改进方案。

## 核心问题

Vision Transformer (ViT) 在 3D 目标检测中表现出色，但其高推理延迟源于**大量 token 的处理开销**。Token 压缩（剪枝和合并）被广泛用于加速，但现有方法的比较缺乏系统性——不同论文使用不同的评估条件，导致结论不一致。

## 方法/架构

论文对 token 压缩策略进行了系统性重新审视：

1. **Token 剪枝（Pruning）**：根据重要性分数移除低价值 token
2. **Token 合并（Merging）**：将相似 token 合并为更少的表示
3. **统一评估框架**：在同一基准下公平比较剪枝和合并策略
4. **发现**：现有方法的优劣高度依赖于具体场景（检测距离、视角数量、场景复杂度）

## 实验结果

- 在多视角 3D 检测基准上系统评估
- 发现**剪枝和合并在不同场景下各有优势**，不存在通用最优解
- 提出**自适应策略**：根据场景特征动态选择压缩方式
- 实现 2-3x 加速，精度损失控制在 1-3% 以内

## 关键洞察

1. **没有银弹**：剪枝和合并不是替代关系，而是互补关系
2. **场景自适应是关键**：固定策略在某些场景下表现很差，需要动态切换
3. **对边缘部署的启示**：token 压缩是 ViT 边缘部署的核心技术，但需要根据硬件特征和场景需求定制

## 为什么重要

手机端的视觉 AI 应用（AR、目标检测、GUI 理解）越来越多使用 ViT 架构。Token 压缩直接影响：
- **GUI Agent 的屏幕理解速度**：Agent 需要实时分析屏幕内容，token 压缩可以大幅降低延迟
- **端侧 3D 感知**：AR 应用需要快速的多视角 3D 检测
- **多模态模型效率**：视觉-语言模型的视觉编码器通常是 ViT，压缩直接影响端侧推理速度

## 关联
- [[multimodal-edge-pruning]] — 多模态边缘剪枝
- [[compressed-sensing-dynamic-reduction]] — 压缩感知动态缩减
- [[sense-less-infer-more]] — 少感知多推理的边缘策略
- [[cora-mobile-gui-safety]] — GUI Agent 中的视觉处理
- [[kl-quantization-ssm-transformer]] — 模型量化与压缩的互补关系
