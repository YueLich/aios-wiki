---
title: "Learning When to Remember: Risk-Sensitive Contextual Bandits for Abstention-Aware Memory Retrieval in LLM-Based Coding Agents"
arXiv: 2604.27283
date: 2026-04-30
tags: [agent-memory, memory-retrieval, security, coding-agents]
reviewer: auto
source: arXiv RSS/API
---

# Learning When to Remember: Risk-Sensitive Contextual Bandits for Abstention-Aware Memory Retrieval in LLM-Based Coding Agents

## 论文基本信息

- **arXiv ID**: 2604.27283
- **作者**: Mehmet Iscan
- **提交日期**: 2026-04-30
- **类别**: cs.CL, cs.AI, cs.LG

## 摘要

基于 LLM 的编码 Agent 越来越依赖外部记忆来复用先前的调试经验、修复轨迹和仓库级操作知识。然而，检索到的记忆只在当前失败与之前失败真正兼容时才有用——栈跟踪、终端错误、路径或配置症状的表面相似性可能导致不安全的记忆注入。本文将 issue-memory 使用重新定义为选择性、风险敏感的控制问题，而非纯 top-k 检索问题。提出 RSCB-MC（Risk-Sensitive Contextual Bandit Memory Controller），决定 Agent 应该：不用记忆、注入最优解决方案、总结多个候选、执行高精度或高召回检索、弃权、或请求反馈。系统通过 pattern-variant-episode schema 存储可重用 issue 知识，将检索证据转换为固定的 16 维上下文状态。

## 核心贡献

1. **风险敏感记忆控制**：不只是检索相关记忆，而是判断「是否应该使用记忆」，避免有害注入。
2. **RSCB-MC 架构**：情境 bandits 控制器，支持 6 种记忆使用策略（不用/注入/总结/高精度/高召回/弃权）。
3. **Pattern-Variant-Episode Schema**：结构化存储 issue 知识，支持可解释的检索决策。
4. **16 维固定状态表示**：将检索上下文压缩为固定维度，适合在线学习和实时决策。

## 为什么重要

这是首个将「何时不用记忆」作为核心问题而非「如何更好检索」的研究。在编码 Agent 场景中，不安全的记忆复用可能导致错误的代码修改被应用，引发生产环境事故。RSCB-MC 通过引入风险敏感性，允许 Agent 在不确定时主动「弃权」，这对安全性要求高的移动端 Agent 场景同样关键。

## 与移动端/端侧相关性

- 移动端编码 Agent（如移动端代码助手）面临同样的记忆复用安全问题
- 16 维固定状态特征适合端侧部署——计算开销小，适合资源受限设备
- 弃权机制（abstention）对高风险操作（支付、删除数据等）尤其重要，与移动端权限管理相关
