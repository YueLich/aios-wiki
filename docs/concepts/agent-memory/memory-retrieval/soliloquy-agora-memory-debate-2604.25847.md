---
title: "From Soliloquy to Agora: Memory-Enhanced LLM Agents with Decentralized Debate for Optimization Modeling"
arXiv: 2604.25847
date: 2026-04-28
tags: [agent-memory, memory-retrieval, multi-agent, optimization]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Jianghao Lin, Zi Ling, Chenyu Zhou, Tianyi Xu
- **提交日期**: 2026-04-28
- **方向**: 记忆检索 / 多Agent辩论 / 优化建模

## 摘要

优化建模支撑了物流、制造、能源和公共服务等领域的现实决策，但当前LLM从自然语言需求可靠地解决此类问题仍具挑战性。本文提出Agora-Opt，一个模块化的Agent化优化建模框架，结合去中心化辩论与读写记忆库。多个Agent团队独立产生端到端解决方案，通过结果 grounding 的辩论协议协调解决分歧，记忆库存储经过求解器验证的产物和历史分歧解决方案，支持免训练的持续改进。

## 核心贡献

1. **去中心化多Agent辩论**：多个Agent独立求解，通过辩论协调，而非中心化协调
2. **读写记忆库**：
   - 存储求解器验证过的 artifacts（最优解、中间结果）
   - 存储历史分歧的解决方案（避免重复分歧）
3. **结果 grounding 的辩论协议**：辩论基于求解器验证的事实，而非猜测
4. **免训练的持续改进**：利用记忆而非微调实现能力提升
5. **跨 backbone 和方法灵活性**：减少对基础模型的依赖，支持跨模型迁移

## 方法详解

**记忆库设计**：
- **Verifiable Artifacts**：经过求解器验证的完整解决方案
- **Disagreement Resolutions**：历史分歧及解决方案的模式库
- **Query-记忆匹配**：给定新问题，检索相似历史问题及解决方案

**辩论协议**：
1. 各Agent独立求解，产生候选方案
2. 方案提交给求解器验证
3. 验证结果作为辩论证据
4. 基于证据进行辩论，淘汰错误方案
5. 保留正确方案到记忆库

**记忆读写操作**：
- 读（Read）：给定当前问题，检索相似历史问题和解决方案
- 写（Write）：新问题解决后，将验证过的产物写入记忆

## 为什么重要

优化建模是LLM Agent的重要应用场景，但现有方法缺乏持续改进机制。Agora-Opt通过记忆库实现跨问题的知识积累，去中心化辩论避免了单点失败，辩论结果接地于求解器验证保证了可靠性。

## 与端侧/移动端的相关性

- 记忆库设计适合在边缘设备上部署
- 去中心化辩论可在多设备间分布式执行
- 免训练特性减少计算和存储开销
- 物流优化、能源调度等场景可在边缘服务器运行
