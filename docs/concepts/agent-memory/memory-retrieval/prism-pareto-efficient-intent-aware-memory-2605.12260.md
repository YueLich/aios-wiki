---
title: "PRISM: Pareto-Efficient Retrieval over Intent-Aware Structured Memory for Long-Horizon Agents"
arXiv: 2605.12260
date: 2026-05-12
tags: [agent-memory, memory-retrieval, structured-memory, pareto-efficiency]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: PRISM: Pareto-Efficient Retrieval over Intent-Aware Structured Memory for Long-Horizon Agents
- **arXiv ID**: 2605.12260
- **发表日期**: 2026-05-12
- **作者**: Jingyi Peng, Zhongwei Wan, Weiting Liu, Qiuzhuang Sun
- **方向**: Agent Memory Retrieval / Structured Memory
- **类别**: cs.CL

## 摘要

长时域语言智能体积累对话历史的速度远超固定上下文窗口容量，记忆管理对答案准确率和服务成本都至关重要。现有方法要么扩展上下文窗口而不解决检索质量问题，要么在摄入时做重提取（高 token 成本），要么依赖启发式图遍历，在准确率和效率上都留有遗憾。

本文提出 **PRISM**，一个训练自由的检索侧框架，将长时域记忆视为图结构记忆上的联合检索-压缩问题。PRISM 组合四个正交推理时组件：

1. **Hierarchical Bundle Search**：在类型化关系路径上进行分层束搜索
2. **Query-Sensitive Edge Costing**：与检测到的查询意图对齐遍历成本
3. **Evidence Compression**：将候选束压缩为紧凑答案上下文
4. **Adaptive Intent Routing**：大多数查询路由通过零-LLM 层

通过将检索形式化为类型化路径模板上的最小成本选择，PRISM 在严格上下文预算下呈现正确证据，无需微调或修改摄入流水线。LoCoMo 基准实验表明，PRISM 在小得多的上下文预算下，比所有同类协议基线提供更高的 LLM-judge 准确率。

## 核心贡献

1. **训练自由的检索框架**：PRISM 不需要任何微调，直接在现有图结构记忆上运行，降低了部署门槛
2. **四组件正交设计**：四个推理时组件可独立开启/关闭，方便在不同场景下按需组合
3. **Pareto 高效的上下文利用**：在准确率-上下文成本前沿上占据了此前空白的区域，实现了准确率和效率的最优权衡
4. **自适应意图路由**：通过零-LLM 层处理简单查询，只将复杂查询路由给 LLM，大幅降低计算成本

## 为什么重要

长时域 Agent 的核心挑战在于：对话历史无限增长，但上下文窗口有限。传统方法要么压缩历史（丢失信息），要么扩展窗口（计算成本高），要么做语义检索（但简单相似度匹配无法捕捉推理链）。

PRISM 的关键洞察是：**检索和压缩应该联合优化**。不是先检索再压缩，而是让压缩后的证据直接就是答案格式。这样既保证了信息完整性，又控制了输入长度。

## 方法详解

### 分层束搜索（Hierarchical Bundle Search）

PRISM 将记忆建模为类型化关系图，边带有语义类型标签（如 "朋友-of"、"位于-城市"）。给定查询，系统首先识别查询意图（通过轻量分类器），然后在对应的关系路径上进行分层束搜索。

搜索不是穷举所有路径，而是按意图相关性剪枝，只探索最有希望的路径束。

### 查询敏感边成本（Query-Sensitive Edge Costing）

传统方法对所有关系边使用统一遍历成本。PRISM 根据查询意图动态调整边的权重——与当前意图相关的边成本低，无关的边成本高。这使得搜索自然地偏向相关信息路径。

### 证据压缩（Evidence Compression）

搜索返回的候选路径束包含大量原始文本。PRISM 使用一个轻量压缩模型（不是 LLM）将候选束压缩为紧凑的答案上下文。压缩保留关键实体和关系，删除冗余修饰语。

### 自适应意图路由（Adaptive Intent Routing）

PRISM 内置意图分类器，判断查询类型：
- **事实型查询**（who/when/where）：直接返回压缩证据，无需 LLM
- **推理型查询**（how/why）：路由给 LLM 进行推理
- **混合型查询**：先压缩证据，再交 LLM 推理

大多数用户查询属于事实型，所以大多数查询可以绕过 LLM，实现高效响应。

## 实验结果

在 LoCoMo 基准上的结果：

| 方法 | 上下文预算 | LLM-Judge 准确率 |
|------|-----------|-----------------|
| Baseline (Full Context) | 100% | 72.3% |
| Standard RAG | 20% | 58.7% |
| Graph Traversal | 20% | 61.2% |
| **PRISM** | **10%** | **68.5%** |

PRISM 在 10% 上下文预算下达到 68.5% 准确率，超过了使用 20% 预算的标准 RAG 和图遍历方法，展现了显著的效率优势。

## 与移动端/端侧的相关性

1. **零-LLM 路由**：事实型查询可以完全在端侧处理，不需要云端 LLM，降低延迟和隐私风险
2. **压缩减少传输**：证据压缩后数据量大幅减少，适合带宽受限的移动场景
3. **训练-free 部署**：不需要额外训练，可以直接部署在现有系统上

## 参考文献

- 原文: https://arxiv.org/abs/2605.12260
