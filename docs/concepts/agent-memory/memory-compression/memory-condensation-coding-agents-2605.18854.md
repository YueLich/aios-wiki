---
title: "Evaluating Memory Condensation Strategies for Coding Agents in Data-Driven Scientific Discovery"
arXiv: 2605.18854
date: 2026-05-13
tags: [agent-memory, memory-compression, coding-agents, scientific-discovery]
reviewer: auto
source: arXiv API
---

## 核心贡献

本文系统评估了 8 种**记忆凝结策略**（Memory Condensation Strategies）在代码 Agent 中的效果，研究对象是数据驱动科学发现任务。背景：代码 Agent 在长时域任务中积累大量上下文，固定上下文窗口迫使从业者在截断和任务失败之间选择。

**关键发现：**
- **凝结器不影响假设质量**：测试的凝结器均未显著改变假设质量
- **LLM-based 凝结器增加成本**：token 成本增加 24-94%
- **工具输出屏蔽效果最佳**：屏蔽工具调用输出可实现 8.6% 的净节省
- **最优凝结器因领域和任务长度而异**：科学领域和任务长度影响最优选择

## 为什么重要

此前没有系统性比较来指导记忆凝结策略选择。本研究填补了这一空白，为科学发现场景中的 Agent 上下文管理提供了实证指导。

## 与端侧/移动端相关性

- **成本效益**：8.6% 净节省对资源受限的端侧部署意义重大
- **工具调用优化**：屏蔽工具输出是最简单有效的策略
- **跨领域泛化**：结论适用于不同领域的代码 Agent

## 八种凝结策略评估

| 策略类型 | Token 成本变化 | 假设质量影响 |
|---------|--------------|------------|
| 滑动窗口 | 降低 | 无显著变化 |
| LLM 摘要 | +24-94% | 无显著变化 |
| 工具输出屏蔽 | -8.6% | 无显著变化 |
| 混合方法 | 因配置而异 | 无显著变化 |

## 研究设计

- **任务**：60 个 DiscoveryBench 任务，跨越 6 个科学领域（480 总评估）
- **模型**：GPT-4o
- **评估指标**：假设质量、Token 成本

## 参考文献

（参考文献待从原文补充）
