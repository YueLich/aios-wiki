---
title: "ECHO: Continuous Hierarchical Memory for Vision-Language-Action Models"
arXiv: 2605.10993
date: 2026-05-09
tags: [agent-memory, multimodal-memory, embodied-memory]
reviewer: auto
source: arXiv RSS/API
---

# ECHO: Continuous Hierarchical Memory for Vision-Language-Action Models

## 论文基本信息

- **arXiv ID**: 2605.10993
- **作者**: Yanbin Hu, Jin Cui, Jiayi Lu, Ruixuan Yang, Jun Ye, Boran Zhao, Xingyu Chen, Xuguang Lan, Pengju Ren
- **机构**: 浙江大学等
- **发表日期**: 2026-05-09
- **类别**: cs.RO (Robotics)
- **代码**: 暂无公开代码链接

## 摘要

记忆容量是决定视觉-语言-动作（VLA）模型在长程操作任务中性能的关键因素。现有的记忆增强架构主要依赖线性或扁平的存储方式，缺乏对操作类别的结构化先验和层级组织。这种缺陷阻碍了高效的经验检索，并限制了在新任务组合上的泛化能力。

本文提出 **ECHO**（Experience Consolidation and Hierarchical Organization），一种在连续层级空间（Continuous Hierarchical Space）中运行的新型记忆框架。ECHO 通过双曲线自编码器（hyperbolic autoencoder）将 VLA 隐藏状态映射到该空间，利用双曲线度量与蕴含约束机制，将经验向量组织为支持自上而下检索的语义记忆树。同时，背景整合机制通过几何插值与结构分裂持续优化记忆树，在连续空间中支持虚拟记忆合成。

ECHO 被集成到 π₀ 基础模型中。在 LIBERO 上的评估及初步真实世界实验表明了方法的有效性：在 LIBERO-Long 上相比 π₀ 基线实现了 12.8% 的绝对执行成功率提升，同时在跨套件未见长程任务上改善了组合泛化能力。

## 核心贡献

### 1. 连续层级空间（Continuous Hierarchical Space）
将 VLA 隐藏状态映射到双曲线空间（hyperbolic space），利用其自然的双曲率特性表达层级化的语义关系，比欧氏空间更高效。

### 2. 语义记忆树（Semantic Memory Tree）
基于双曲线度量组织的树形记忆结构，支持：
- 自上而下的检索（从高层概念到具体经验）
- 蕴含约束机制确保子节点语义被子节点包含
- 结构性先验使检索更高效

### 3. 背景整合机制（Background Consolidation）
- **几何插值**：在连续空间中通过几何插值整合新经验
- **结构分裂**：当记忆容量超限时自动分裂节点
- **虚拟记忆合成**：在连续空间中生成未见过的组合经验

### 4. 12.8% 绝对性能提升
在 LIBERO-Long 基准上从 π₀ 基线显著提升，证明了层级记忆对长程任务的重要性。

## 为什么重要

VLA 模型（如 π₀）在长程机器人操作任务中表现受到记忆容量的根本限制。现有方法将所有历史经验平等地存储在扁平记忆中，检索时缺乏语义结构，导致：
1. 检索效率低（需要扫描大量不相关的经验）
2. 泛化能力差（无法利用高层语义关系）

ECHO 通过引入层级化的语义结构解决了这个问题，使 VLA 能够像人类一样从高层到低层逐步回忆相关经验。这一方法在移动机器人、嵌入式代理等资源受限场景中尤为重要——层级结构可以实现有优先级的记忆管理。

## 与移动端/端侧的相关性

- **移动机器人**：ECHO 的层级记忆结构天然支持有优先级检索，对移动机器人内存受限环境有意义。
- **端侧 VLA**：双曲线空间的高效压缩表示使层级记忆可以在端侧部署。
- **持续经验积累**：背景整合机制使机器人能够不断从新经验中学习并优化记忆结构，无需全量重训。

## 参考文献

本文参考文献待从原文补充。
