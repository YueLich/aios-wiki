---
title: "Lifecycle-Aware Federated Continual Learning in Mobile Autonomous Systems"
arXiv: 2604.20745
date: 2026-04-22
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Lifecycle-Aware Federated Continual Learning in Mobile Autonomous Systems

## 论文基本信息

- **作者**: Zitai Wang, Chen Shi, Jiaxn Liu 等
- **arXiv**: https://arxiv.org/abs/2604.20745
- **领域**: cs.LG, cs.RO

## 摘要

联邦持续学习（FCL）使分布式自主车队能够跨扩展任务生命周期协作适应地形类型变化。但当前方法面临几个关键挑战：1）使用统一保护策略，不考虑不同网络层对遗忘的敏感度差异；2）主要关注训练期间防止遗忘，不解决累积漂移的长期影响；3）依赖理想化模拟，无法捕获分布式车队的真实异构性。论文提出生命周期感知双时间尺度 FCL 框架，包含训练时（预遗忘）预防和（后遗忘）恢复。实验在真实 rover 测试平台上验证，系统级鲁棒性结果确认了设计的有效性。

## 核心贡献

1. **Dual-timescale FCL Framework**: 训练时预防 + 恢复的双时间尺度框架
2. **Layer-selective Rehearsal**: 针对不同网络层敏感度差异的层级选择排练策略
3. **Rapid Knowledge Recovery**: 长期累积漂移后的快速知识恢复策略
4. **8.3% mIoU 提升**: 在真实 rover 测试平台上验证
5. **31.7% vs Fine-tuning**: 相对传统微调提升 31.7%

## 研究背景与问题

FCL 应用于移动自主系统时面临独特挑战：分布式车队需要在保护隐私的前提下协作学习，但现有方法忽视了网络层差异、长期漂移和现实异构性。

## 核心方法

1. **Training-time Prevention**: 层级选择排练策略减轻训练期间即时遗忘
2. **Post-forgetting Recovery**: 长期累积漂移后的快速知识恢复
3. **Layer Sensitivity Analysis**: 分析不同层对遗忘的敏感度差异
4. **Real-world Deployment**: 在真实 rover 测试平台验证，而非仅模拟

## 为什么重要

这是首个在真实移动平台上系统验证 FCL 有效性的研究。移动自主系统是 FCL 的重要应用场景，该研究填补了从模拟到真实部署的差距。

## 与移动端/端侧相关性

1. **移动自主系统**: 自动驾驶、机器人等分布式移动系统的核心挑战
2. **隐私保护**: 联邦学习在本地数据不上传的情况下协作学习
3. **资源异构**: 不同移动设备计算能力不同，层级敏感度策略有直接价值
4. **长期部署**: 车队等长期运行系统，累积漂移问题尤为突出
