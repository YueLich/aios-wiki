---
title: "CuSearch: Curriculum Rollout Sampling via Search Depth for Agentic RAG"
arXiv: 2605.11611
date: 2026-05-12
tags: [agent-memory, memory-retrieval, agentic-rag]
reviewer: auto
source: arXiv API
---

# 核心理解

CuSearch 研究了一个关键问题：在基于强化学习可验证奖励（RLVR）训练 Agentic RAG 系统时，如何对检索轨迹进行采样才能最大化训练效率？现有方法对所有轨迹均匀采样，但轨迹的"搜索深度"差异很大——深轨迹包含更多检索决策点，能提供更密集的监督信号。

# 核心贡献

1. **Search-Depth Greedy Allocation (SDGA)**：一种批量级算子，将固定更新预算重新分配给更深搜索轨迹的采样方法。

2. **SDGA-Auto**：自动瞄准当前批次中最深轨迹，产生隐式训练对齐课程。

3. **SDGA-Phase**：显式推进课程阈值，当更深轨迹足够丰富时进行转换。

4. **发现**：每轨迹搜索深度是检索监督密度的可靠、无标注代理，可作为 RLVR 训练中批次内深度分布的动态指示器。

# 为什么重要

论文建立了 per-trajectory search depth 作为可靠注释的检索监督密度代理，在 ZeroSearch 上比标准 GRPO 提升高达 11.8 个精确匹配点。这对端侧 Agent 的记忆检索训练有直接意义——更深轨迹包含更多记忆访问模式，是更好的训练信号。

# 论文核心方法

现有 RLVR 方法从均匀采样的轨迹中优化策略，隐式假设所有轨迹同等信息。但轨迹搜索深度差异巨大（从简单单步检索到复杂多步推理链），且这种异质性随训练增长（批次内深度分布向更高值移动）。均匀采样对此变化"盲目"。

CuSearch 提出 SDGA 框架：
- **SDGA-Auto**：在每个训练步骤中，瞄准当前批次中最深的可用轨迹
- **SDGA-Phase**：当更深轨迹变得足够丰富时，阶段性推进课程阈值

实验在多种模型和检索框架上进行，CuSearch 始终优于均匀采样。

# 与移动端/端侧相关性

端侧 Agent 的记忆检索训练数据稀缺，CuSearch 的课程采样策略能更高效利用有限的专家演示。搜索深度作为无标注代理，使端侧在线学习成为可能。

# 参考文献

参考文献待从原文补充。
