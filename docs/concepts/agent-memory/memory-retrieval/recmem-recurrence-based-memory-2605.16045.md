---
title: RecMem: Recurrence-based Memory Consolidation for Efficient and Effective Long-Running LLM Agents
arXiv: 2605.16045
date: 2026-05-15
tags: [agent-memory, memory-retrieval, memory-consolidation]
reviewer: auto
source: arXiv RSS/API
---

## 论文信息

- **作者**: Zijie Dai, Shiyuan Deng, Sheng Guan, Yizhou Tian, Xin Yao
- **发表**: 2026-05-15
- **类别**: cs.CL
- **机构**: （待从原文补充）

## 摘要（原文翻译）

记忆系统通常将用户与 Agent 的交互组织为可检索的外部记忆，对克服 LLM 有限上下文窗口、实现长期运行 Agent 至关重要。然而，现有记忆系统对每条交互都调用 LLM 进行记忆提取，这种"急切的记忆整合"方案导致大量 token 消耗。为解决此问题，RecMem 提出重新思考**何时应该进行记忆整合**。RecMem 将交互存储在"下意识记忆层"，并使用轻量级 embedding 模型进行编码以供检索。只有当观察到语义相似交互的**持续重复**时，才调用 LLM 提取情景记忆和语义记忆。这种基于重复的整合策略之所以有效，是因为这些交互对应一个信息丰富的语义集群，值得提取和总结。为提高准确性，RecMem 还引入了语义精炼机制，恢复记忆提取中遗漏的细粒度事实。实验表明，RecMem 在将三个 SOTA 记忆系统的记忆构建 token 成本降低高达 **87%** 的同时，准确性甚至有所提升。

## 核心贡献

1. **下意识记忆层（Subconscious Memory Layer）**：新交互先用轻量级 embedding 存储，无需 LLM 调用，只在需要时触发提取
2. **基于重复的记忆整合（Recurrence-based Consolidation）**：当相似语义交互持续出现时才调用 LLM，大幅降低计算成本
3. **语义精炼机制（Semantic Refinement）**：恢复提取过程中遗漏的细粒度事实，保证记忆质量
4. **87% token 成本降低**：相比三个 SOTA 记忆系统，在提升准确率的同时实现数量级的效率提升

## 为什么重要

长期运行 Agent 的核心挑战是上下文窗口有限，记忆系统是解决此问题的关键。但现有方案对每条交互都调用 LLM，token 消耗巨大，难以规模化。RecMem 证明：**不需要对每条交互都做 LLM 级记忆提取**——只有"反复出现的模式"才值得深层提取。这一发现为构建真正可持续的长期 Agent 提供了新的工程思路。

## 与移动端/端侧的相关性

端侧 Agent（如手机助手、可穿戴设备）资源受限，无法频繁调用大模型。RecMem 的"下意识记忆层 + 按需 LLM 提取"两级架构天然适合端侧：
- **日常简单查询**：仅用 embedding 检索，无需唤醒大模型
- **重复模式检测**：积累一定重复后触发 LLM 提取，实现个性化记忆
- **87% token 节省**：在移动端带宽和算力受限的情况下意义重大

## 参考文献

- Dai, Z., et al. (2026). RecMem: Recurrence-based Memory Consolidation for Efficient and Effective Long-Running LLM Agents. arXiv:2605.16045.
