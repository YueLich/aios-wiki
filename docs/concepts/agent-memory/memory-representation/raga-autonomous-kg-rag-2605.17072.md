---
title: "RAGA: Reading-And-Graph-building-Agent for Autonomous Knowledge Graph Construction and Retrieval-Augmented Generation"
arXiv: 2605.17072
date: 2026-05-16
tags: [agent-memory, memory-representation, knowledge-graph, RAG]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: RAGA: Reading-And-Graph-building-Agent for Autonomous Knowledge Graph Construction and Retrieval-Augmented Generation
- **arXiv ID**: 2605.17072
- **发表日期**: 2026-05-16
- **作者**: Chengrui Han, Zesheng Cheng（来自国内机构）
- **方向**: 知识图谱构建、检索增强生成、Agent记忆系统
- **类别**: cs.AI / cs.CL

## 摘要

现有LLM驱动的知识图谱（KG）构建方法主要采用无状态的批量处理流程，在跨chunk语义关系捕获、实体消歧和构建过程可解释性方面存在结构性问题。这些局限性损害了KG质量、检索精度和高风险领域部署的信任度。

RAGA（Reading And Graph-building Agent）是一个基于LLM的自主KG构建与检索融合框架。RAGA提供支持完整KG生命周期 CRUD 操作的原子工具集，并将"读取-搜索-验证-构建"认知约束嵌入ReAct工具循环。KG-向量同步机制实现混合符号-向量检索，而证据锚定验证将每个知识条目链接到其源文本以实现可审计的溯源。

在QASPER科学QA数据集子集上的初步实验表明，RAGA的融合检索优于零样本基线，KG集成为答案质量和证据质量带来了可衡量的提升。

## 核心贡献

1. **自主KG构建Agent框架**：将KG构建从批量处理流程转变为Agent驱动的自主操作，支持完整的创建-读取-更新-删除生命周期
2. **Read-Search-Verify-Construct认知约束**：嵌入ReAct工具循环的认知约束，确保构建过程的每一步都可验证
3. **KG-向量同步机制**：实现混合符号（KG）与向量检索的统一，兼顾精确查询和语义相似性
4. **证据锚定验证**：每个知识条目直接链接到源文本，支持可审计的知识溯源

## 为什么重要

知识图谱作为Agent的外部记忆系统，需要解决三个核心问题：
- **动态更新**：传统批量构建无法处理知识的动态演变
- **质量保证**：无状态流程缺乏实体验证和关系消歧能力
- **可审计性**：RAG系统需要知道知识来源以避免幻觉

RAGA通过Agent化框架同时解决这三个问题，其KG-向量同步机制对于混合记忆系统（符号+向量）有重要参考价值。

## 与移动端/端侧相关性

当前RAGA设计面向通用领域知识图谱构建。向端侧迁移的潜在方向：
- 在边缘设备上部署轻量级KG构建Agent（Qwen3-4B级别）
- 利用KG压缩技术实现移动端知识存储
- 研究端侧隐私保护KG构建（数据不出设备）

## 参考文献

（参考文献待从原文补充）
