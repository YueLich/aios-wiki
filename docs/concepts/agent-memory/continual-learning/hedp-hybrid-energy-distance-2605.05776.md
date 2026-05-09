---
title: "HEDP: A Hybrid Energy-Distance Prompt-based Framework for Domain Incremental Learning"
arXiv: 2605.05776
date: 2026-05-07
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# HEDP: A Hybrid Energy-Distance Prompt-based Framework for Domain Incremental Learning

## 论文基本信息

- **arXiv ID**: 2605.05776
- **发表时间**: 2026-05-07
- **作者**: Yu Feng, Zhen Tian, Haoran Luo, Xie Yu, Diancheng Cheng et al.
- **方向**: 持续学习、域增量学习、灾难性遗忘
- **类别**: cs.AI

## 摘要

域增量学习（Domain Incremental Learning）是持续学习的关键场景，要求模型在不重新训练的情况下持续适应新数据域。然而，域迁移经常导致严重的性能下降。

本文提出 **Hybrid Energy-Distance Prompt (HEDP)**，一种受 Helmholtz 自由能启发的域增量框架。HEDP 包含：

1. **能量正则化损失**：增强域表示的可分离性
2. **混合能量-距离加权机制**：融合基于能量和基于距离的线索，改善域选择和泛化

在 CORe50 等多个基准测试上的实验表明，HEDP 在未见域上实现了 2.57% 的准确率提升，有效缓解了灾难性遗忘并增强了开放世界适应性。

## 核心贡献

1. **Helmholtz 自由能启发的学习框架**：将物理概念引入持续学习
2. **能量正则化损失**：增强域表示的判别性和可分离性
3. **混合能量-距离加权机制**：融合多种线索优化域选择
4. **2.57% 准确率提升**（CORe50 等基准）

## 为什么重要

1. **理论基础**：将 Helmholtz 自由能的概念形式化地引入域增量学习
2. **实用有效**：在多个基准上验证了方法的有效性
3. **开放世界适应性**：增强模型在新域上的泛化能力

## 与移动端/端侧的相关性

1. **通用框架**：不依赖特定架构，适合在各种端侧设备上部署
2. **效率与性能平衡**：能量和距离机制的组合在计算效率和性能之间取得平衡
3. **持续适应能力**：适合需要在部署后持续学习新域的移动应用

## 关键方法细节

### 能量正则化
- 基于 Helmholtz 自由能理论
- 增强不同域表示的分离度
- 防止域间的知识干扰

### 混合加权机制
- **能量线索**：基于能量模型估计样本难度和域相关性
- **距离线索**：基于样本到决策边界的距离
- **融合策略**：自适应组合两种线索指导学习和推理

## 实验结果

- CORe50 等多个基准测试
- 2.57% 准确率提升
- 有效缓解灾难性遗忘
- 增强开放世界适应性

## 参考文献

- 域增量学习相关研究
- Helmholtz 自由能与机器学习
- 灾难性遗忘与持续学习
