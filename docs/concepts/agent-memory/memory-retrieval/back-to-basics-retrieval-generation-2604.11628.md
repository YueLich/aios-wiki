---
title: "Back to Basics: Let Conversational Agents Remember with Just Retrieval and Generation"
arXiv: 2604.11628
date: 2026-04-13
tags: [agent-memory, memory-retrieval, minimalist-memory, conversational-memory]
reviewer: auto
source: arXiv RSS/API
---

# Back to Basics: Let Conversational Agents Remember with Just Retrieval and Generation

## 论文信息

- **arXiv ID**: 2604.11628
- **作者**: Yuqian Wu, Wei Chen, Zhengjun Huang, Junle Chen, Qingxiang Liu
- **发表日期**: 2026-04-13
- **方向**: 记忆的检索与利用、极简记忆架构
- **代码**: 待补充

## 摘要（翻译）

现有对话记忆系统依赖复杂的层级摘要或强化学习来管理长期对话历史，但在对话增长时仍容易受到上下文稀释影响。

本文提出不同视角：主要瓶颈可能不在记忆架构，而在**潜在知识流形中的信号稀疏效应**（Signal Sparsity Effect）。通过受控实验，我们识别了两个关键现象：

1. **决定性证据稀疏**（Decisive Evidence Sparsity）：随着会话变长，相关信号变得越来越孤立，导致基于聚合的方法急剧退化
2. **双层冗余**（Dual-Level Redundancy）：会话间干扰和会话内对话填充物都引入大量非信息性内容，阻碍有效生成

基于这些洞察，我们提出 **\method**，一种回归基础的极简框架，仅依赖检索和生成，通过**回合隔离检索**（Turn Isolation Retrieval, TIR）和**查询驱动剪枝**（Query-Driven Pruning, QDP）。TIR 用最大激活策略替代全局聚合来捕获回合级信号，QDP 移除冗余会话和对话填充物以构建紧凑高密度证据集。

在多个基准上的广泛实验证明 \method 在多样化设置中实现稳健性能，持续优于强基线，同时在 token 和延迟上保持高效率，为对话记忆建立了新的极简基线。

## 核心贡献

### 1. 信号稀疏效应的诊断

**决定性证据稀疏**：
- 随着对话历史增长，相关信号在嵌入空间中变得更孤立
- 聚合方法（平均、attention 加权）会被无关信号稀释
- 这解释了为什么复杂架构在长对话上退化

**双层冗余**：
- 会话间冗余：不同会话中相似的非实质性对话
- 会话内冗余：对话中的填充词、客套话等

### 2. TIR：回合隔离检索

与全局聚合不同，TIR 的策略：
- 对每个候选回合独立计算相关性得分
- 取最大激活而非平均
- 只返回 top-k 最相关回合（而非全部）

这避免了低相关回合的稀释效应。

### 3. QDP：查询驱动剪枝

两步剪枝策略：
1. **会话层剪枝**：移除整会话中与查询无关的会话
2. **回合层剪枝**：移除会话内的非信息性对话

通过查询相关性指导剪枝决策，而非启发式规则。

## 实验结果

在多个基准上持续优于强基线，包括：
- 长对话设置（最受益于稀疏效应缓解）
- 多会话场景
- 复杂推理查询

同时在 token 使用和延迟上保持高效率。

## 为什么重要

Back to Basics 的核心洞察是：对话记忆问题的根源不在架构复杂度，而在**信号稀疏和冗余**。

关键贡献：
1. **诊断先行**：首次系统量化了信号稀疏和双层冗余的问题
2. **简单即有效**：TIR + QDP 比复杂层级架构更有效
3. **为极简主义正名**：证明了简单方法在适当设计下可以超越复杂方案

## 与端侧/移动端相关性

1. **低复杂度**：无层级架构，适合资源受限的移动端
2. **Token 高效**：减少上下文 token 对移动端带宽和内存都是利好
3. **延迟低**：无复杂聚合操作，检索延迟更低
