---
title: "AdaTKG: Adaptive Memory for Temporal Knowledge Graph Reasoning"
arXiv: "2605.07121"
date: "2026-05-08"
tags: [agent-memory, memory-representation, knowledge-graph, temporal-reasoning]
reviewer: auto
source: arXiv API
---

## 摘要

Temporal knowledge graphs (TKGs) represent time-stamped relational facts and support a wide range of reasoning tasks over evolving events. However, existing methods produce entity representations that are static at the entity level — each representation is a function of learned parameters only and retains no trace of the interactions in which the entity has participated. This paper departs from this static view and proposes that each entity be modeled as an adaptive process whose representation is refined every time the entity participates in a fact.

## 核心贡献

1. **自适应记忆机制**：AdaTKG 为每个实体维护一个记忆（memory），每次实体参与交互时更新，记忆随时间累积，预测随更多交互到来而改善。

2. **指数移动平均更新**：将记忆更新实例化为可学习的指数移动平均（Exponential Moving Average），由单个共享标量控制，而非每个实体独立学习参数，使 AdaTKG 能够处理训练时未见过的实体（unseen entities）。

3. **在线记忆累积**：记忆随每次观察到的交互在线积累，预测质量随交互增加而提升。

## 关键洞察

**传统 TKG 方法的局限**：现有方法产生的是静态实体表示——每个表示只是学习参数的函数，不保留实体参与过的交互痕迹。这意味着模型无法"记住"实体的历史交互上下文。

**AdaTKG 的解决思路**：将实体建模为自适应过程（adaptive process），而非静态向量。每次实体参与事实（fact），其表示就被更新一次，记忆是累积性的。

## 方法细节

- **记忆更新机制**：可学习的指数移动平均（learnable EMA），由单一共享标量governed，而非为每个实体独立学习参数
- **处理 unseen 实体**：由于使用共享标量而非per-entity参数，AdaTKG 可以泛化到训练时未见过的实体
- **在线学习**：记忆在推理时持续更新，不需要批量重训练

## 实验结果

在多个 TKG 基准数据集上，持续优于基线方法，验证了自适应记忆的有效性。代码已公开。

## 为什么重要

这是第一篇明确提出"实体应该拥有累积性自适应记忆"的 TKG 论文。核心贡献——用 EMA 作为记忆更新机制——对 Agent 记忆系统的设计有直接启发：

- **在线记忆更新**：Agent 与环境每次交互后，其关于世界中实体/概念的记忆应该动态更新
- **共享记忆机制**：使用单一机制控制所有实体的记忆更新，而非为每个实体存储独立参数（更高效）
- **处理新实体**：能够对未见实体快速建立记忆，不需要重新训练

## 与移动端/端侧相关性

- 记忆更新机制轻量（单一共享标量），适合端侧部署
- 在线学习模式适合持续交互的端侧场景（如手机助手、机器人）
- 可作为端侧知识图谱记忆的底层机制

## 参考文献

- GitHub: https://github.com/seunghan96/AdaTKG
