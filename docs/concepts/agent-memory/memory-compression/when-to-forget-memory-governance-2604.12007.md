---
title: "When to Forget: A Memory Governance Primitive"
arXiv: 2604.12007
date: 2026-04-13
authors: ["Baris Simsek"]
tags: [agent-memory, memory-compression, memory-governance, selective-forgetting]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.12007
- **作者**: Baris Simsek
- **提交日期**: 2026-04-13
- **方向**: 记忆治理 / 遗忘机制 / 记忆质量评估

## 摘要（全文翻译）

Agent 记忆系统积累经验，但目前缺乏记忆质量治理的原则性操作指标——即当 Agent 的任务分布变化时，决定哪些记忆值得信任、压制或弃用的指标。现有的写入时重要性评分是静态的；动态管理系统使用 LLM 判断或结构性启发式，而非**结果反馈**。

本文提出 **Memory Worth (MW)**：一种每个记忆的**双计数器（two-counter）**信号，跟踪记忆与成功结果 versus 失败结果共同出现的频率，提供了一个轻量级、有理论基础的老化检测、检索压制和弃用决策基础。

本文证明了在固定检索机制和最小探索条件下，MW 几乎必然收敛到条件成功概率 **p+(m) = Pr[y_t = +1 | m in M_t]**——即给定记忆 m 被检索时任务成功的概率。重要的是，p+(m) 是**关联量而非因果量**：它衡量的是结果共现，而非因果贡献。本文认为这对记忆治理仍然是有用的操作信号，并在一个**地面真值已知**的受控合成环境中验证。

## 核心贡献

1. **Memory Worth (MW) 指标**：基于双计数器的记忆价值信号，追踪记忆与成功/失败结果的共现频率
2. **理论收敛保证**：证明 MW 在温和条件下收敛到条件成功概率 p+(m)
3. **三个治理操作**：基于 MW 的老化检测、检索压制、记忆弃用决策
4. **关联 vs 因果的澄清**：p+(m) 是关联量而非因果量，但这不妨碍其作为操作指标的用处

## 为什么重要

这是记忆治理领域的里程碑论文，首次为"何时遗忘"提供了**可量化、有理论保证的操作指标**。现有方法依赖 LLM 主观判断或结构性启发式，MW 则通过结果反馈自然地发现哪些记忆真正有助于任务成功：

- **非主观**：不需要 LLM 评估记忆重要性，直接从结果学习
- **有理论基础**：收敛到条件成功概率不是经验观察，而是有数学证明的
- **可操作性**：MW 直接可用于决定压制还是检索某条记忆

## 与端侧/移动端的相关性

**高度相关**。移动端 Agent 资源受限，无法无限积累记忆，需要有效的遗忘机制。MW 的双计数器设计非常轻量（只需要两个整数），可以在设备端高效实现。通过追踪记忆与成功/失败结果的共现，设备可以在本地学习哪些记忆真正有用，无需云端 LLM 做评估。

## 关键引文

> "p+(m) is an associational quantity, not a causal one: it measures outcome co-occurrence rather than causal contribution. We argue this is still a useful operational signal for memory governance"

---

## 方法细节

### 双计数器机制

每个记忆 m 维护两个计数器：
- **成功计数器 C+(m)**：记忆被检索且任务成功时 +1
- **失败计数器 C-(m)**：记忆被检索且任务失败时 +1

MW = C+(m) / (C+(m) + C-(m))，即条件成功概率的蒙特卡洛估计。

### 收敛性

在固定检索分布（stationary retrieval regime）和最小探索条件（minimum exploration condition）下，MW 几乎必然收敛到 p+(m)。

### 三种治理操作

1. **Staleness detection（老化检测）**：MW 持续下降的記憶值得标记为老化
2. **Retrieval suppression（检索压制）**：MW 低于阈值的记忆在检索时被压制
3. **Deprecation（弃用）**：MW 极低的记忆被主动删除
