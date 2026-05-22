---
title: "TA-Mem: Tool-Augmented Autonomous Memory Retrieval for LLM in Long-Term Conversational QA"
arXiv: "2603.09297"
date: "2026-03-10"
tags: [agent-memory, memory-retrieval, tool-augmented, long-context]
reviewer: auto
source: arXiv RSS/API
---

# TA-Mem: Tool-Augmented Autonomous Memory Retrieval for LLM in Long-Term Conversational QA

## 论文基本信息

- **arXiv ID**: 2603.09297
- **发表日期**: 2026-03-10
- **作者**: Mengwei Yuan, Jianan Liu, Jing Yang, Xianyou Li, Weiran Yan, Yichao Wu, Penghao Liang
- **方向**: Memory Retrieval, Tool-Augmented LLM, Long-Context QA
- **类别**: cs.IR, cs.CL

## 摘要

大语言模型（LLM）在各种领域的文本推理任务中展现出强大能力，但上下文窗口的限制给长程推理任务带来了挑战，亟需记忆存储系统。现有的记忆存储方案（如情景笔记和图谱表示）已有多项研究，但检索方法仍主要依赖预定义工作流或基于嵌入的静态相似度 top-k 检索。为解决这一灵活性不足的问题，本文提出 TA-Mem，一种工具增强的自主记忆检索框架。

## 核心贡献

### 1. 三组件协同架构

TA-Mem 由三个核心组件构成：

**（1）记忆提取 LLM Agent** — 将输入内容按语义相关性自适应分块（chunking），提取为结构化笔记。采用自适应分块策略，而非固定长度切分，能够保留语义完整性。

**（2）多索引记忆数据库** — 支持多种查询方式，包括：
- 基于键值（key-based）的精确查找
- 基于相似度（similarity-based）的向量检索
不同类型的记忆内容采用最适合的索引策略。

**（3）工具增强的检索 Agent** — 能够根据用户输入自主选择数据库提供的合适工具，探索记忆并决定是继续迭代还是最终生成回答。具备工具选择和迭代推理能力。

### 2. 自适应工具选择机制

传统记忆检索是单次静态查询，TA-Mem 的检索 Agent 可以根据已获取的记忆内容动态决定是否需要进一步检索，体现了真正的自主性和适应性。

### 3. LoCoMo 数据集验证

在 LoCoMo 数据集（长程对话问答基准）上取得了显著的性能提升，超越多个基线方法。消融分析还表明不同问题类型下的工具使用模式存在差异，进一步验证了方法的自适应性。

## 为什么重要

当前 Agent 记忆系统的检索模块普遍薄弱——要么依赖预定义流程（缺乏灵活性），要么只做简单的相似度匹配（无法深层推理）。TA-Mem 通过引入工具增强的自主探索机制，让记忆检索变成了一个主动的、迭代的、多工具协作的过程。这对构建真正能够处理长程对话的 AI Agent 具有重要意义。

## 与移动端/端侧的相关性

虽然论文本身聚焦于通用 LLM 场景，但其多索引数据库设计思路和工具选择机制对于端侧轻量记忆系统的构建有参考价值。多索引架构可以根据不同硬件能力选择检索路径，实现性能与资源消耗的平衡。

## 参考文献

（参考文献待从原文补充）
