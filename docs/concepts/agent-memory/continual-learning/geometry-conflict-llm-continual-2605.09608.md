---
title: "Geometry Conflict: Explaining and Controlling Forgetting in LLM Continual Post-Training"
arXiv: 2605.09608
date: 2026-05-10
tags: [agent-memory, continual-learning, memory-compression]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **标题**: Geometry Conflict: Explaining and Controlling Forgetting in LLM Continual Post-Training
- **arXiv ID**: 2605.09608
- **发表日期**: 2026-05-10
- **作者**: Yuanyi Wang, Yifan Yang, Su Lu, Yanggan Gu, Pengkai Wang
- **方向**: 持续学习 / 记忆压缩
- **类别**: cs.LG

## 摘要

持续后训练旨在为大语言模型扩展新知识、新技能和新行为，但尚不清楚顺序更新何时能实现能力迁移、何时会引发灾难性遗忘。现有方法通过顺序微调、重放、正则化或模型合并来缓解遗忘，但缺乏判断何时整合新更新有益或有害的标准。本文从任务几何角度研究 LLM 持续后训练：用参数更新表示每个后训练任务，研究更新诱导的协方差几何与演化模型状态的几何之间的关系。核心发现：遗忘可视为状态相对的更新整合失败，当任务诱导的协方差几何与模型状态的先前更新几何不对齐时发生。顺序更新在与其保持兼容时迁移，当状态相对几何冲突升高时产生干扰。基于此提出 Geometry-Conflict Wasserstein Merging（GCWM），一种无数据更新整合方法，通过高斯 Wasserstein 重心构建共享 Wasserstein 度量，并使用几何冲突来门控几何感知校正。在 Qwen3 0.6B-14B 上的域连续和和能力连续设置中均优于无数据基线。

## 核心贡献

1. **几何冲突理论**：提出用任务参数更新的协方差几何来解释遗忘，遗忘源于任务几何与模型状态的冲突
2. **状态相对兼容性**：顺序更新迁移的条件是保持与先前更新形成的模型状态的兼容性
3. **GCWM 方法**：无数据更新整合方法，使用 Wasserstein 度量和几何冲突作为控制信号
4. **跨规模验证**：在 Qwen3 0.6B-14B 多规模模型上验证有效性，无需重放数据

## 为什么重要

本文提供了理解和控制 LLM 持续后训练中灾难性遗忘的统一理论框架。核心洞察——遗忘是"状态相对的更新整合失败"——对于设计 Agent 的记忆系统至关重要。当 Agent 需要不断学习新技能时，需要评估新记忆是否会与已有知识产生几何冲突。GCWM 的无数据特性使其特别适合端侧持续学习场景。

## 与端侧/移动端的相关性

- **无数据持续学习**：GCWM 不需要重放数据，适合存储资源受限的移动端
- **模型合并**：几何冲突理论可用于判断何时合并不同专业化的模型版本
- **增量更新**：为边缘设备上的 LLM 个性化提供理论基础和实践方法
- **兼容性判断**：新技能学习前可评估与现有能力的冲突程度，决定是否学习或如何整合

## 参考文献

本文参考文献待从原文补充。
