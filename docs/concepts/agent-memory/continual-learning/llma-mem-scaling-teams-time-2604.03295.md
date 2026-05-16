---
title: "Scaling Teams or Scaling Time? Memory Enabled Lifelong Learning in LLM Multi-Agent Systems"
arXiv: 2604.03295
date: 2026-03-27
tags: [agent-memory, continual-learning, multi-agent, memory-topology]
reviewer: auto
source: arXiv
---

## 论文基本信息

- **作者**: Shanglin Wu, Yuyang Luo, Yueqing Liang, Kaiwen Shi, Yanfang Ye
- **发表**: 2026-03-27
- **类别**: cs.MA / cs.AI

## 摘要

大语言模型多智能体系统沿两条轴线扩展：增加智能体数量（scaling teams）和通过积累经验持续改进（scaling time）。现有研究分别考察了这两条轴线，但二者在现实成本约束下的交互关系尚不清晰。本文提出了一个联 合 scaling 框架，将团队规模和终身学习能力纳入统一考量，并研究记忆设计如何影响这一格局。具体地，本文提出 LLMA-Mem——一个支持灵活记忆拓扑的 LLM 多智能体终身记忆框架。在 MultiAgentBench 上的编码、研究和数据库环境评估表明，LLMA-Mem 在降低成本的同时持续优于基线。分析还揭示了一个非单调 scaling 景观：更大规模的团队并不总带来更好的长期性能，当记忆能更好地支持经验复用时，更小的团队反而可以超越更大的团队。这些发现将记忆设计定位为更有效、更高效地随时间扩展多智能体系统的实践路径。

## 核心贡献

1. **联合 scaling 视角**：首次将团队规模和终身学习能力统一建模，研究二者交互
2. **LLMA-Mem 框架**：支持灵活记忆拓扑的多智能体终身记忆框架
3. **非单调 scaling 规律**：揭示团队规模与记忆质量之间的复杂关系
4. **经验复用的关键作用**：证明记忆设计是 scaling time 维度的核心杠杆

## 为什么重要

对多智能体系统的扩展性研究提供了新视角：不应单纯堆叠智能体数量，而应重视记忆设计以支持经验复用，从而以更低成本实现更好的长期性能。

## 与移动端/端侧的相关性

论文聚焦多智能体协作系统，记忆拓扑设计（集中式 vs 分布式）对移动端资源受限场景有参考意义，但核心贡献在于多智能体架构层面的 scaling 规律。

---
*（参考文献待从原文补充）*
