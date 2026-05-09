---
title: "AOI: Context-Aware Multi-Agent Operations via Dynamic Scheduling and Hierarchical Memory Compression"
arXiv: 2512.13956
date: 2025-12-15
authors: ["Zishan Bai", "Hanxuan Chen", "Jing Luo", "Ziyi Ni", "Enze Ge", "Jiacheng Shi", "Yichao Zhang", "Jiayi Gu", "Zhimo Han", "Riyang Bao", "Junfeng Hao"]
tags: [agent-memory, multi-agent, hierarchical-memory, memory-compression, IT-operations, context-aware]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2512.13956
- **发表日期**: 2025-12-15
- **作者**: Zishan Bai, Hanxuan Chen, Jing Luo, Ziyi Ni, Enze Ge, Jiacheng Shi, Yichao Zhang, Jiayi Gu, Zhimo Han, Riyang Bao, Junfeng Hao
- **方向**: 多层记忆架构（Working-Episodic-Semantic 三层记忆）

## 摘要

**背景**：云原生架构（微服务和动态编排）使现代 IT 基础设施极其复杂和动荡。传统系统面临关键瓶颈：信息处理低效、任务协调差、上下文连续性丢失。

**方法**：AOI（AI-Oriented Operations）提出三_specialized agents + LLM-based Context Compressor 框架：
1. 动态任务调度策略：根据实时系统状态自适应优先级调度
2. 三层记忆架构：Working Memory（工作记忆）、Episodic Memory（情景记忆）、Semantic Memory（语义记忆），优化上下文保留和检索

**实验结果**：72.4% 上下文压缩率同时保留 92.8% 关键信息，任务成功率 94.2%，MTTR（平均修复时间）降低 34.4%。

## 核心贡献

1. **三层记忆架构**：首次为 IT 运维场景设计 Working-Episodic-Semantic 三层记忆，明确区分不同类型上下文的管理策略
2. **动态任务调度**：根据实时状态自适应调度，而非静态规则
3. **高压缩率保留**：72.4% 压缩下仍保留 92.8% 关键信息，远超简单压缩方法
4. **生产级验证**：在合成和真实基准测试上验证，包括实际 IT 运维场景

## 为什么重要

多 Agent 系统中的记忆管理是核心挑战：

- **上下文爆炸**：多 Agent 协作产生海量上下文，无记忆管理无法 scale
- **IT 运维场景**：故障诊断和修复需要长期（语义）记忆、事件（情景）记忆和实时（工作）记忆的协同
- **工程实用性**：AOI 不是理论框架，而是针对实际 IT 运维问题的解决方案

## 与端侧/移动端的相关性

三层记忆架构对端侧多 Agent 系统有参考价值：

- **分层记忆管理**：工作记忆保留即时上下文，情景记忆保留事件历史，语义记忆保留结构化知识
- **压缩率与质量权衡**：72.4% 压缩保留 92.8% 信息，对移动端有限存储直接适用
- **多 Agent 协调**：边缘设备群协作时，记忆压缩和调度策略可降低通信开销

## 参考文献

- arXiv: 2512.13956 | https://arxiv.org/abs/2512.13956
