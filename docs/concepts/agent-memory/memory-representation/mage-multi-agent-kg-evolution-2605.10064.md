---
title: "MAGE: Multi-Agent Self-Evolution with Co-Evolutionary Knowledge Graphs"
arXiv: "2605.10064"
date: "2026-05-11"
tags: [agent-memory, memory-representation, knowledge-graph, multi-agent]
reviewer: auto
source: arXiv RSS/API
---

# MAGE: Multi-Agent Self-Evolution with Co-Evolutionary Knowledge Graphs

## 论文基本信息

- **arXiv ID**: 2605.10064
- **发表日期**: 2026-05-11
- **作者**: Ruiyi Yang, Zechen Li, Hao Xue, Imran Razzak, Flora D. Salim
- **方向**: 记忆表示 / 知识图谱 / 多智能体
- **类别**: cs.AI

## 摘要（翻译）

自进化语言模型智能体必须决定下一步学习什么以及如何保留已学知识。现有系统通常将跨迭代知识作为自然语言反馈、平面情景记忆或隐式强化信号保存，均无法在推理时有效支持冻骨干（frozen backbone）的执行。本文提出 MAGE（Multi-Agent Graph-guided Evolution），一个将自知识外化为四子图协同演化知识图的框架。其经验子图（experience subgraph）同时存储教师撰写的失败修正和学习者自身过去的正确推理轨迹，作为任务条件化引导检索给冻执行模型使用。在演化过程中，知识图谱、任务级搜索赌博机和技能级路由赌博机从同一奖励流更新，而学习者骨干保持不变。

## 核心贡献

1. **四子图协同演化知识图谱**：将自进化知识分解为经验子图、成功修正子图、任务搜索子图和技能路由子图，四图协同更新
2. **冻骨干执行模型**：知识图谱作为冻骨干推理时的外部引导信号，无需更新模型权重
3. **经验子图的双向记忆**：同时存储教师撰写的失败修正和学习者自身的成功推理轨迹，两者互补
4. **结构化分析**：证明仅追加记忆增长、有界课程覆盖和任务过滤检索共同支持冻学习者演化的稳定改进

## 为什么重要

MAGE 解决了自进化智能体中的核心挑战：如何在保持冻骨干的同时实现持续改进。通过将知识外化为可协同演化的知识图谱，MAGE 使得多个智能体可以共享和积累经验，同时保留各自的学习轨迹。这对端侧部署的终身学习智能体特别有价值，因为模型权重更新代价高昂，而知识图谱的增量构建成本相对较低。

## 与移动端/端侧相关性

- 知识图谱可独立于模型权重更新，适合资源受限的端侧环境
- 冻骨干 + 外部知识图谱的架构减少了边端模型更新的需求
- 多智能体协同演化支持分布式边端场景

## 参考文献

见原论文
