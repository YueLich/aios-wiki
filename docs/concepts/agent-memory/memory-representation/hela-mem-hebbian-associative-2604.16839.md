---
title: "HeLa-Mem: Hebbian Learning and Associative Memory for LLM Agents"
arXiv: 2604.16839
date: 2026-04-18
tags: [agent-memory, memory-representation, continual-learning, Hebbian-learning]
reviewer: auto
source: arXiv RSS/API
---

# HeLa-Mem: Hebbian Learning and Associative Memory for LLM Agents

## 论文信息

- **arXiv ID**: 2604.16839
- **作者**: Jinchang Zhu, Jindong Li, Cheng Zhang, Jiahong Liu, Menglin Yang
- **发表日期**: 2026-04-18
- **方向**: 记忆的表示与存储、持续学习
- **开源代码**: https://github.com/ReinerBRO/HeLa-Mem

## 摘要（翻译）

长期记忆是大型语言模型智能体面临的关键挑战——固定的上下文窗口无法在扩展交互中保持连贯性。现有记忆系统将对话历史表示为非结构化的嵌入向量，通过语义相似性进行检索。这种范式无法捕捉人类记忆的联想结构——相关经验通过重复共同激活逐渐强化相互连接。

受认知神经科学启发，HeLa-Mem 识别了生物记忆的三种核心机制：联想（association）、巩固（consolidation）和扩散激活（spreading activation），这三种机制在当前研究中基本缺失。

HeLa-Mem 提出一种受生物启发的记忆架构，将记忆建模为具有Hebbian学习 dynamics 的动态图，采用双层组织：
1. **情景记忆图**（Episodic Memory Graph）：通过共同激活模式演化的情景记忆图
2. **语义记忆存储**（Semantic Memory Store）：通过Hebbian Distillation填充的语义记忆库

实验在 LoCoMo 上验证了优越性能，同时使用的上下文 token 大幅减少。

## 核心贡献

### 1. 三种生物记忆机制的对应实现

| 生物机制 | HeLa-Mem 实现 |
|---------|--------------|
| 联想 (Association) | 动态图结构，边权重随共同激活增强 |
| 巩固 (Consolidation) | Hebbian Distillation 将情景记忆转化为语义记忆 |
| 扩散激活 (Spreading Activation) | 查询时通过图传播激活相关记忆节点 |

### 2. 双层记忆架构

**情景记忆图层**：
- 将每次交互建模为图节点，边表示共同激活关系
- 边的权重随经验重复而增加（Hebbian rule: "neurons that fire together, wire together"）
- 支持时序和语义两种边类型

**语义记忆存储层**：
- 由一个 Reflective Agent（反思智能体）识别密集连接的记忆中枢
- 将这些中枢蒸馏为结构化的、可重用的语义知识
- 双重路径设计同时利用语义相似性和习得联想

### 3. Hebbian Distillation 机制

将高频共同激活的记忆节点群蒸馏为语义记忆条目，类似于人类记忆系统中情节记忆向语义记忆的转化过程。这一机制解决了：
- 情景记忆的细节丢失问题
- 语义记忆的冷启动问题

## 实验结果

- **LoCoMo Benchmark**：四个问题类别上均达到优越性能
- **Token 效率**：显著减少上下文 token 使用量（相比全上下文回放）
- 代码已开源

## 为什么重要

HeLa-Mem 填补了 LLM Agent 记忆中缺乏生物合理性联想机制的空白。现有记忆系统大多只做语义相似性检索，而人类记忆的核心是**联想结构**——相关经验通过重复共同激活逐渐强化连接。这种联想结构对于：
- 跨会话连贯推理
- 相关经验的自适应复用
- 记忆的渐进式组织

都有重要意义。HeLa-Mem 首次在 LLM Agent 记忆中系统性地引入这三种生物记忆机制。

## 与端侧/移动端相关性

1. **图结构存储效率**：动态图的边压缩存储比全量向量存储更紧凑，适合端侧资源受限场景
2. **Token 减少**：显著减少的上下文 token 使用量对移动端带宽和计算资源都是利好
3. **渐进式学习**：Hebbian learning 的增量特性天然适合端侧的持续学习场景
