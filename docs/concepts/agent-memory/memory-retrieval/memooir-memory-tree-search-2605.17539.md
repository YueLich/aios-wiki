---
title: "MEMOIR: Memory-Guided Tree Search with Cross-Branch Knowledge Transfer for LLM Solver Synthesis"
arXiv: "2605.17539"
date: "2026-05-17"
tags: [agent-memory, memory-retrieval, tree-search, combinatorial-optimization]
reviewer: auto
source: arXiv RSS/API
---

## 核心贡献

**MEMOIR** 提出了一种记忆引导的树搜索框架，用于 LLM 求解器综合（Solver Synthesis）。核心贡献：

1. **双层记忆层次结构**：
   - **Branch-local memory（分支局部记忆）**：在单个分支迭代单一算法设计时，保留基于执行细节的细化信息
   - **Global memory（全局记忆）**：存储跨分支的压缩算法摘要和失败模式总结

2. **反射步骤（Reflection Step）**：在分支终止时提炼这些摘要，实现跨分支知识迁移，而不污染未来上下文的低级调试追踪

3. **在 7 个组合优化问题上验证**，涵盖调度、路由、装箱和几何设计，MEMOIR 达到 96.7% 的解有效性（比最强基线高 9.2 分），在匹配每方法执行预算下平均归一化分数提升 7.3 分

## 为什么重要

组合优化（CO）是从物流到芯片设计的决策基础，小的质量提升就能带来可观的经济价值。现有树搜索和进化智能体在并行细化候选轨迹时没有显式知识迁移机制，导致重复约束违反和相似的算法族收敛。MEMOIR 通过记忆引导探索实现稳定、一致的改进——在四个问题的三次独立运行中，MEMOIR 的运行间有效性标准差比所有评估基线低一个数量级以上。

## 与移动端/端侧相关性

MEMOIR 的记忆层次结构设计（分支局部+全局）可用于边缘设备上的本地优化任务。跨分支知识迁移减少了对重复计算的需求，与端侧资源的约束性相契合。其树搜索框架也可应用于移动端的任务规划与调度。

## 参考文献

Fatemeh Haji, Javier Delarosa Quiros, Peyman Najafirad. "Memory-Guided Tree Search with Cross-Branch Knowledge Transfer for LLM Solver Synthesis." arXiv:2605.17539, 2026.
