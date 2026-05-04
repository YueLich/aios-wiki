---
title: "Learning When to Remember: Risk-Sensitive Contextual Bandits for Abstention-Aware Memory Retrieval in LLM-Based Coding Agents"
arXiv: 2604.27283
date: 2026-04-30
authors: "Mehmet Iscan (Yildiz Technical University, PythaLab)"
tags: [agent-memory, memory-retrieval, risk-sensitive, coding-agents, contextual-bandits]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv**: 2604.27283v1
- **发表**: 2026-04-30
- **作者**: Mehmet Iscan (Yildiz Technical University, PythaLab)
- **方向**: 记忆检索 / 风险敏感决策
- **开源**: 待确认

---

## 问题背景

LLM编程Agent依赖外部记忆来重用历史调试经验。但**表面相似性经常具有误导性**——不同根因可能暴露相似的堆栈跟踪、终端错误、路径或配置症状。

不安全的记忆注入会导致：
- Agent锚定在错误修复策略上
- 消耗宝贵上下文预算
- 放大幻觉修复

---

## 核心方法：RSCB-MC

**RSCB-MC** = Risk-Sensitive Contextual Bandit Memory Controller

### 核心思想重构

将记忆使用从"纯top-k检索问题"重新定义为**选择性、风险敏感的控制问题**。

### 行动空间（6种选择）

1. **不用记忆** (no memory)
2. **注入top 1解决方案** (inject top resolution)
3. **总结多个候选** (summarize multiple candidates)
4. **执行高精度检索** (high-precision retrieval)
5. **执行高召回检索** (high-recall retrieval)
6. **弃权/请求反馈** (abstain / ask for feedback)

### Pattern-Variant-Episode Schema

存储可重用问题知识的结构化表示，捕获：
- 问题的深层结构（而非表面症状）
- 变体模式（pattern variants）

### 16维上下文状态

将检索证据转化为固定16维状态向量，捕获：
| 维度类别 | 具体特征 |
|---|---|
| 相关性 | 与当前问题的匹配程度 |
| 不确定性 | 检索结果的置信度 |
| 结构兼容性 | 历史方案与当前结构的匹配 |
| 反馈历史 | 之前使用该记忆的结果 |
| 误报风险 | 误报的可能性 |
| 延迟 | 检索延迟 |
| Token成本 | 记忆注入的token开销 |

### 奖励设计（关键创新）

**故意对误报记忆注入的惩罚 > 错过重用的惩罚**

这是风险敏感设计的核心——宁可漏掉好记忆，也不用坏记忆。

---

## 为什么重要

首个将**风险敏感决策框架**系统性地应用于记忆检索控制的论文。在代码生成Agent（上下文极度珍贵）中，区分"什么时候不用记忆"和"用什么记忆"同样重要。

### 与移动端/端侧的相关性

- **上下文预算紧张**的端侧场景：弃权(abstention)机制直接节省token
- **资源敏感的RL控制器**：16维状态向量的计算开销可接受
- **嵌入式Agent**：内存和计算双重受限，风险敏感的检索控制比高召回更重要
