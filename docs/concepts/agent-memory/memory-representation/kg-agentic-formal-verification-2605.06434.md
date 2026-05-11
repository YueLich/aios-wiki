---
title: "Knowledge Graphs, the Missing Link in Agentic AI-based Formal Verification"
arXiv: "2605.06434"
date: "2026-05-07"
tags: [agent-memory, knowledge-graph, agentic-AI, formal-verification]
reviewer: auto
source: arXiv API
---

## 摘要

Recent advances in Large Language Models (LLMs) have enabled workflows that generate SystemVerilog Assertions (SVAs) from natural-language specifications, with the potential to accelerate Formal Verification (FV). However, high-quality assertion synthesis remains challenging because specifications are often ambiguous or incomplete and critical micro-architectural details reside in the Register Transfer Level (RTL).

Many existing approaches treat the specification and RTL as loosely structured text, which weakens specification-to-RTL grounding and leads to semantic mismatches and frequent syntax failures. This work addresses these limitations with a verification-centric Knowledge Graph (KG) constructed from structured Intermediate Representations (IRs) extracted from the specification, RTL, and formal-tool feedback, including syntax diagnostics, Counterexamples (CEXs), and coverage reports.

## 核心贡献

1. **以验证为中心的知识图谱**：从规范、RTL 和形式化工具反馈中提取结构化中间表示（IRs），构建验证-centric KG，链接需求、设计层次、信号、假设和属性。

2. **多智能体工作流**：多智能体工作流查询和更新 KG，生成 SVAs，驱动三个 refinement loops：
   - 语法修复（syntax repair）：由工具诊断指导
   - CEX修正（CEX-guided correction）：使用 trace links
   - 覆盖率导向的属性增强（coverage-directed property augmentation）

3. **多轮迭代 refinement**：KG 存储设计知识，支持多轮 LLM 查询和更新，实现持续改进的验证循环。

## 关键洞察

**现有方法的局限**：将规范和 RTL 视为松散结构的文本，specification-to-RTL grounding 弱，导致语义不匹配和语法失败。

**KG 作为记忆中介**：知识图谱作为 LLM 的结构化记忆，存储：
- 需求（requirements）
- 设计层次结构（design hierarchy）
- 信号（signals）
- 假设（assumptions）
- 属性（properties）

这提供了可追溯的（traceable）、基于设计的上下文（design-grounded context）。

## 为什么重要

这是第一篇将知识图谱明确作为 Agent 记忆系统用于形式化验证的论文。对 Agent 记忆系统的设计有重要启发：

1. **KG 作为结构化记忆**：KG 不仅是静态知识存储，还可以是 Agent 推理的 active working memory，支持查询和更新
2. **多智能体 + 记忆**：多个智能体协作查询和更新同一个 KG，实现分布式记忆共享
3. **记忆 refinement 循环**：基于反馈（诊断、CEX、覆盖率）的记忆精化机制

## 与移动端/端侧相关性

- 端侧 Agent 在执行复杂任务时同样需要维护结构化记忆（类似 KG 的任务状态、约束、历史决策）
- 多智能体 + 共享记忆的模式可用于端侧多模型协作
- 轻量级 KG 推理引擎可在端侧运行

## 实验结果

在 7 个基准设计上的评估表明：KG 上下文检索改善了规范到 RTL 的 grounding，持续生成可编译的 SVAs，语法修复开销低。形式覆盖率范围 78.5%–99.4%，但收敛性呈现设计依赖性，复杂时间和算术推理对当前 LLM 能力仍有挑战。

## 参考文献
