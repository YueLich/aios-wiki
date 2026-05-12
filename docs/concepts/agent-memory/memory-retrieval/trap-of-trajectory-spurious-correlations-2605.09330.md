---
title: "The Trap of Trajectory: Towards Understanding and Mitigating Spurious Correlations in Agentic Memory"
arXiv: "2605.09330"
date: "2026-05-10"
tags: [agent-memory, memory-retrieval, reliability, spurious-correlations]
reviewer: auto
source: arXiv API
---

# The Trap of Trajectory: Towards Understanding and Mitigating Spurious Correlations in Agentic Memory

## 摘要

Agent 记忆使 LLM 能跨上下文持久化信息并复用决策，但同时引入新脆弱性：**虚假相关**（spurious correlations）——记忆携带错误关联证据，将错误推理传播到下游决策。现有研究对此风险探索不足。本文从两方面入手：（1）**建立基准**，通过因果结构识别轨迹层面记忆中的典型虚假模式，发现记忆在干净输入上提升推理但在虚假模式存在时放大依赖；（2）**提出 CAMEL**，一种即插即用的校准方法，在写入和检索阶段对多种记忆架构运作，在消除虚假模式依赖的同时保持或提升干净输入性能，并可抵御针对性攻击。

## 核心贡献

1. **首个 Agent 记忆虚假相关基准**：系统识别三类因果结构的典型虚假模式，诊断显示现有记忆系统在干净/虚假输入上存在根本性矛盾（提升前者但放大后者）。
2. **CAMEL 校准方法**：在写入时和检索时对记忆系统进行校准，无需重新训练、即插即用、架构无关。
3. **对抗鲁棒性**：针对校准的针对性攻击下 CAMEL 仍保持鲁棒。
4. **干净输入性能维持**：消除虚假依赖的同时不损害正常推理能力。

## 为什么重要

这是首个系统揭示 **Agent 记忆可靠性**问题的论文。虚假相关广泛存在但此前未被充分重视——记忆被误用为"正确性证明"而非"证据来源"，CAMEL 提供了无需重训的实用解法，对部署可靠性要求高的生产系统有直接价值。

## 与移动端/端侧相关性

移动端 Agent 对可靠性要求极高（隐私数据、离线场景），虚假相关风险在本地化记忆场景下尤为关键，CAMEL 的轻量即插即用特性适合端侧部署。

## 参考文献

- CAMEL 方法详见原论文
