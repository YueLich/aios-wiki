---
title: "EvoMemBench: Benchmarking Agent Memory from a Self-Evolving Perspective"
arXiv: 2605.18421
date: 2026-05-18
tags: [agent-memory, benchmark, self-evolving, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: 现有 agent 评测主要关注推理、规划和执行能力，而 memory 作为 agent 的核心组件却缺乏系统性评测。此外，现有 memory 评测都是静态的——评测时 agent 记忆内容固定，无法评估记忆的**动态演化**能力。

**方法**: EvoMemBench 从自进化视角构建 agent memory 评测基准，系统评估记忆系统在三方面的演化能力：

### 评测维度

1. **记忆获取（Acquisition）**：agent 能否从新经验中有效提取并存储新知识
2. **记忆更新（Update）**：当新信息与旧记忆冲突时，agent 能否正确更新
3. **记忆检索（Retrieval）**：在演化了多轮之后，检索精度能保持多少

### 任务类型

- 知识积累型：agent 需要在多轮对话中逐步构建对用户偏好/项目背景的完整理解
- 干扰对抗型：记忆中有误导性信息，agent 需要在演化过程中识别并纠正
- 遗忘触发型：记忆自然增长后，agent 需要主动决定何时遗忘/压缩

## 核心贡献

1. **首个自进化视角 memory 评测基准**：填补了 memory 动态演化能力评测的空白
2. **多粒度评测体系**：从 token 级别、对话级别、任务级别三层评估记忆质量
3. **揭示主流 memory agent 的演化瓶颈**：测试显示即使是 GPT-4 + memory 系统，在第 10 轮后检索精度平均下降 35%
4. **开源评测框架**：提供可扩展的评测框架，支持研究者添加新领域和任务类型

## 为什么重要

Self-evolving 是下一代 agent 的核心特征——能够从交互中持续学习并改进自身。EvoMemBench 首次体系化地评估了这一能力在 memory 维度的表现，其发现的问题（精度随轮次下降、干扰更新失效）直接指明了未来研究的方向。

## 与移动端/端侧的相关性

端侧 agent 特别需要 self-evolving memory——设备上的 agent 需要在不依赖云端的情况下持续适应用户习惯。EvoMemBench 的评测发现对设计"设备端持续学习记忆系统"有直接参考价值。

## 参考文献

- Wang, Y., et al. (2026). EvoMemBench: Benchmarking Agent Memory from a Self-Evolving Perspective. arXiv:2605.18421.
