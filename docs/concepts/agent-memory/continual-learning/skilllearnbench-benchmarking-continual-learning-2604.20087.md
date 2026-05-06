---
title: "SkillLearnBench: Benchmarking Continual Learning Methods for Agent Skill Generation on Real-World Tasks"
arXiv: 2604.20087
date: 2026-04-22
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# SkillLearnBench: Benchmarking Continual Learning Methods for Agent Skill Generation on Real-World Tasks

## 论文基本信息

- **作者**: 郭晓晨 等
- **arXiv**: https://arxiv.org/abs/2604.20087
- **代码**: https://github.com/cxcscmu/SkillLearnBench

## 摘要

技能已成为 LLM Agent 执行复杂真实任务的事实标准方式，但如何自动有效地学习技能仍不清楚。SkillLearnBench 是首个评估持续技能学习方法的基准，包含来自真实技能分类学的 20 个已验证、技能依赖的任务，跨 15 个子领域，在三个层次评估：技能质量、执行轨迹和任务结果。使用该基准评估最近的持续学习方法，发现所有方法都优于无技能基线，但持续增益仍不可靠——没有方法在所有任务和 LLM 上领先，更强 LLM 扩展也不可靠地有帮助。

## 核心贡献

1. **SkillLearnBench 基准**: 首个评估 Agent 持续技能学习的系统性基准
2. **多层次评估**: 技能质量、执行轨迹、任务结果三层次评估
3. **20 真实任务**: 来自真实技能分类学的 20 个已验证任务，15 个子领域
4. **方法比较**: 系统比较多种 CL 方法在技能学习上的表现
5. **关键发现**: 持续学习对清晰可复用工作流的任务有效，对开放性任务无效

## 研究背景与问题

Agent 需要从经验中持续学习新技能，但缺乏系统评估这一能力的基准。现有 CL 基准聚焦于分类/检测任务，不适合评估技能学习这一更复杂的能力。

## 核心方法

1. **Skill Taxonomy Construction**: 从真实世界任务中构建技能分类体系
2. **Multi-level Evaluation**: 技能质量（正确性）、轨迹质量（效率）、任务结果三层次
3. **Method Comparison Framework**: 统一评估设置下比较多种 CL 方法
4. **LLM Backbone Analysis**: 测试不同 LLM 能力下的 CL 方法表现

## 为什么重要

SkillLearnBench 为 Agent 技能持续学习提供了首个系统性评估框架。其发现（强 LLM 不一定带来更好的技能学习、开放性任务仍是挑战）对 Agent 系统的持续学习设计有重要指导意义。

## 与移动端/端侧相关性

1. **端侧技能学习**: 移动端 Agent 需要从用户交互中持续学习技能
2. **资源受限评估**: 基准考虑了计算资源限制下的技能学习效率
3. **个性化技能**: 用户特定技能的持续学习对移动端个性化至关重要
