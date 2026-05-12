---
title: "Cross-Sample Relational Fusion: Unifying Domain Generalization and Class-Incremental Learning"
arXiv: 2605.08839
date: 2026-05-09
tags: [agent-memory, continual-learning, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Cross-Sample Relational Fusion: Unifying Domain Generalization and Class-Incremental Learning
- **arXiv ID**: 2605.08839
- **发表日期**: 2026-05-09
- **作者**: Zhen-Hao Xie, Yan Wang, Hao Sun, Han-Jia Ye, De-Chuan Zhan, Da-Wei Zhou
- **方向**: 持续学习（Continual Learning）/ 灾难性遗忘（Catastrophic Forgetting）
- **类别**: cs.CV

## 摘要

类增量学习（Class-Incremental Learning, CIL）要求系统在学习新类别的同时保留已学知识。然而，在自动驾驶等现实场景中，模型在晴天城市道路训练后，可能需要在农村或高速公路等不同天气和交通模式的环境下运行。这要求模型不仅克服灾难性遗忘，还要有效处理域迁移（domain shift）。

本文提出 **CrOss-sample Relational Fusion (CORF)**——一个同时解决域迁移和灾难性遗忘的统一框架。

**核心方法**：

1. **选择性样本细化（Selective Sample Refinement）**：利用空间贡献图（spatial contribution maps）突出语义信息丰富区域，对训练样本进行选择性精炼，提升泛化能力
2. **自适应样本加权（Adaptive Sample Weighing）**：结合预测置信度，自适应地为样本赋予权重，学习域无关表示（domain-agnostic representations）
3. **级联蒸馏框架（Cascaded Distillation Framework）**：捕捉跨样本关系依赖，跨多个特征层次实现知识迁移，有效缓解遗忘

CORF 可无缝集成到现有 CIL 算法中，在多种基准数据集上取得具有竞争力的性能。

代码已开源：https://github.com/LAMDA-CL/TMM26-CORF

## 核心贡献

1. **统一框架**：首次将域泛化（Domain Generalization）与类增量学习统一在一个框架下，同时解决 domain shift 和 catastrophic forgetting 两个挑战
2. **跨样本关系依赖**：提出跨特征层次捕捉样本间关系依赖的级联蒸馏方法，而非仅蒸馏单样本知识
3. **空间贡献图**：利用空间贡献图定位语义信息丰富区域，指导选择性样本细化
4. **自适应加权机制**：结合预测置信度自适应调整样本权重，增强域无关表示学习

## 为什么重要

传统持续学习方法假设训练和测试分布一致（single-domain），忽视了现实世界中的域迁移问题。例如：

- 自动驾驶模型在晴天训练的视觉特征，可能无法泛化到雨天或夜间
- 机器人在实验室环境学会的操作技能，可能无法迁移到真实家庭环境

CORF 同时关注**遗忘问题**和**泛化问题**，更贴近实际部署需求，代表了持续学习研究从理想实验室设定向真实场景迁移的重要趋势。

## 与记忆系统的关联

CORF 的核心机制与 Agent 记忆系统有深刻关联：

| CORF 机制 | Agent 记忆对应 |
|-----------|---------------|
| 跨样本关系蒸馏 | 记忆压缩中的关联压缩——保留记忆间的关系结构而非独立事实 |
| 选择性样本细化 | 记忆选择性——类似重要性判别，决定哪些记忆值得保留 |
| 自适应样本加权 | 记忆优先级——根据置信度和场景相关性动态调整记忆权重 |
| 域无关表示学习 | 知识迁移——将从特定任务学到的知识抽象为可泛化的表示 |

## 与移动端/端侧相关性

端侧持续学习面临的核心挑战与 CORF 解决的问题高度一致：

- **数据分布漂移**：移动设备上的用户行为分布随时间和场景变化（类似 domain shift）
- **灾难性遗忘**：端侧模型持续学习新任务时容易遗忘旧知识
- **计算效率**：CORF 的级联蒸馏框架相比全模型蒸馏计算开销更小，适合资源受限场景

在端侧持续学习（如移动端个性化推荐、穿戴设备健康监测）中，CORF 的域无关表示学习能力可帮助模型更好地适应用户个体差异和场景变化。

## 参考文献

- Xie et al. "Cross-Sample Relational Fusion: Unifying Domain Generalization and Class-Incremental Learning." arXiv:2605.08839, 2026.
