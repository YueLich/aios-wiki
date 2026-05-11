---
title: "When Stored Evidence Stops Being Usable: Scale-Conditioned Evaluation of Agent Memory"
arXiv: 2605.07313
date: 2026-05-08
tags: [agent-memory, memory-retrieval, evaluation]
reviewer: auto
source: arXiv API
---

## 摘要

现有记忆-Agent 评估仅报告固定快照的准确率或检索质量，无法揭示**证据在无关会话累积时是否仍然可用**。本文提出"规模条件评估协议"（Scale-Conditioned Evaluation Protocol）：对每个查询，固定任务证据，逐步增加无关会话（irrelevant sessions），记录 Agent-Memory 轨迹，输出四项诊断指标：预算一致性可靠性（budget-compliant reliability）、尾部记忆调用负担（tail memory-call burden）、失败状态分解（failure-regime decomposition）以及**可用规模边界**（usable-scale boundary，即可靠性跌破目标值的规模阈值）。在 LongMemEval 和 LoCoMo 上针对 flat/planar/hierarchical 三种记忆接口的实验表明：可靠性衰减并非单一现象。在 LongMemEval 上，HippoRAG 在两调用预算内保持，但随无关会话增加其预算一致性可靠性下降 16-20 个百分点；LiCoMemory 的失败模式与具体 Agent 强相关，Qwen3-8B 超出预算而 Qwen3-32B/235B 在测试范围内保持可靠。结果支持"可规模化的记忆系统声明必须以 Agent、接口、规模范围和交互预算为条件"的框架。

## 核心贡献

1. **规模条件评估协议**：首个系统研究"证据随无关会话增长而衰减"的评估框架
2. **四项诊断指标**：
   - 预算一致性可靠性（budget-compliant reliability）
   - 尾部记忆调用负担（tail memory-call burden）
   - 失败状态分解（failure-regime decomposition）
   - 可用规模边界（usable-scale boundary）
3. **跨接口泛化分析**：flat/planar/hierarchical 三种记忆接口的系统对比
4. **关键发现**：可靠性衰减不是单一现象，与 Agent 能力、接口类型、规模范围、交互预算均相关

## 为什么重要

现有评估只测"能不能找到"，不测"找的东西是否还管用"。在真实场景中，Agent 记忆随时间积累无关信息（会话历史、背景文档等），干扰信号增加导致原本相关的证据变得"不可用"。本文首次提出这个根本性问题并给出量化框架，为实际部署中记忆系统的可靠性评估提供了标准。

## 与移动端/端侧相关性

该评估协议适用于评估任何规模的记忆系统，可帮助判断在资源受限的移动端设备上，给定记忆规模下的系统可靠性阈值，对端侧记忆系统的规模预算设计有直接指导意义。
