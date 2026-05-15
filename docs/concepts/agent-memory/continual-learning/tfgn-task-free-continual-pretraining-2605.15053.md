---
title: "TFGN: Task-Free, Replay-Free Continual Pre-Training Without Catastrophic Forgetting at LLM Scale"
arXiv: 2605.15053
date: 2026-05-14
tags: [agent-memory, continual-learning, catastrophic-forgetting, llm-scale]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

在大语言模型规模上，持续预训练异构文本领域且不使用回放或任务标签，一直是悬而未决的架构难题。现有方法依赖回放缓冲区、任务标识符、扩展性差的正则化惩罚，或仅限句子分类规模的评估。本文提出 TFGN，一种适用于 Transformer 语言模型的架构覆盖层，它产生输入条件化的参数高效更新，同时保持 Transformer 其余部分不变。TFGN 在六个异构文本领域（Prose、Python、Math、Biomedical、Chinese、JavaScript）上，每阶段 1B tokens，跨越三个模型规模（~398M、~739M、~9B）和两种机制（From-Scratch 和 Retrofit），取得了优异表现：在 LLaMA 3.1 8B Retrofit 上实现 -0.007 的后向迁移、HellaSwag 保留率 0.506/0.504/0.510，以及域对之间 >=99.59% 的 L2 正交梯度分离——且无需回放、无需任务 ID、无需 Fisher 惩罚。同一套矩阵还显示出正向的跨域前向迁移：仅通过 Python 训练，LLaMA-8B Retrofit 上留出 JavaScript PPL 下降 26.8%，GPT-2 Medium From-Scratch 上下降 62.0%。基于同一底层架构的两个扩展进一步解决了其他开放问题。扩展 A（闭环元控制层）在 ~398M 规模上额外减少 81% 的遗忘，映射到 Dupoux et al. 的 System A 和 System M 角色。扩展 B（算子级计划向量）以 99.96% 的余弦保真度重塑前向传递行为，跨越 30 个源→目标对。

## 核心贡献

1. **读写分解架构**：前向传递全密集，跨域参数更新结构化，使得先前域的子空间不会被写入。首次在 LLM 规模上同时解决灾难性遗忘、实现闭环自主学习元控制器、携带算子级潜在规划器。

2. **零代价持续学习**：无需回放缓冲区（节省显存）、无需任务标识符（无需任务边界知识）、无需 Fisher 惩罚（无二阶计算开销）。

3. **正向跨域迁移**：不仅防止遗忘，还能从已学领域正向迁移到新领域，如 Python→JavaScript 的显著提升。

4. **闭环元控制层（扩展 A）**：额外减少 81% 遗忘，映射认知科学中的 System A/M 双系统机制。

5. **算子级计划向量（扩展 B）**：99.96% 余弦保真度的前向行为重塑，跨 30 个源→目标域对验证。

## 为什么重要

在 LLM 规模实现真正的持续学习是通往通用智能的关键里程碑。TFGN 的核心洞察——读写分解——为在不遗忘旧知识的前提下持续吸收新知识提供了一条可行路径，且无需复杂的工程基础设施（回放队列）或计算开销（Fisher 矩阵）。这对端侧 Agent 的持续适应能力有直接影响：设备上的 LLM 可以像人类一样边用边学，而无需云端协调。

## 与移动端/端侧的相关性

TFGN 的参数高效特性对端侧 LLM 具有重要参考价值。其核心机制（前向全密集、更新结构化保护旧知识子空间）可转化为轻量级持续学习策略，使移动端模型能在本地持续适应用户交互模式，无需云端回放数据。扩展 A/B 的正交化思想也可用于移动端多任务学习的干扰隔离。

## 方法细节

### 核心架构：TFGN Overlay

TFGN 在预训练 Transformer 基础上添加了一个轻量级架构层：

- **写路径保护**：梯度更新仅写入当前域专属参数区域，先前域参数区域被结构化锁定
- **读路径共享**：前向推理时所有参数全参与，最大化知识共享效率

### 实验配置

| 模型规模 | 机制 | 域数量 | 每域 tokens |
|---------|------|--------|------------|
| ~398M | From-Scratch | 6 | 1B |
| ~739M | Retrofit | 6 | 1B |
| ~9B | Both | 6 | 1B |

### 关键指标

- **后向迁移（BWT）**：-0.007（LLaMA 3.1 8B Retrofit），接近零表示无遗忘
- **HellaSwag 保留率**：0.506-0.510，各域基本持平
- **梯度正交性**：>=99.59% L2 正交分离
- **前向迁移（FWT）**：JavaScript PPL 下降 26.8%（8B）和 62.0%（739M）

### 扩展 A：闭环元控制层

参考 Dupoux et al. 的认知双系统理论，实现 System A（快速适应）和 System M（记忆保留）的计算对应。实验显示额外减少 81% 遗忘（~398M 规模）。

### 扩展 B：算子级计划向量

在学习过程中生成低维计划向量，在推理时条件化激活模式。99.96% 余弦保真度验证了前向行为重塑的有效性。

## 参考文献

- Dupoux et al. (2023). Cognitive Science: System A and System M roles
- Original TFGN paper: https://arxiv.org/abs/2605.15053
