---
title: "LatentRAG: Latent Reasoning and Retrieval for Efficient Agentic RAG"
arXiv: 2605.06285
date: 2026-05-07
tags: [agent-memory, memory-retrieval, agentic-rag]
reviewer: auto
source: arXiv RSS/API
---

# LatentRAG: Latent Reasoning and Retrieval for Efficient Agentic RAG

## 论文基本信息

- **标题**: LatentRAG: Latent Reasoning and Retrieval for Efficient Agentic RAG
- **arXiv ID**: 2605.06285
- **发表日期**: 2026-05-07
- **作者**: Yijia Zheng, Marcel Worring
- **方向**: 记忆检索 · Agentic RAG
- **类别**: cs.CL

## 摘要（原文翻译）

单步检索增强生成（RAG）为简单问答任务提供了融合外部信息的有效途径，但在处理复杂问题时表现吃力。Agentic RAG 将单步检索扩展为多步过程——大语言模型（LLM）充当搜索智能体，生成中间思维和子查询，迭代地与检索系统交互。这种迭代过程因自回归生成冗长的思维和子查询而产生大量延迟。为解决这一局限，本文提出 LatentRAG，一个将推理和检索从离散语言空间迁移到连续潜在空间的新框架。与现有显式方法不同，LatentRAG 不生成自然语言思维和子查询，而是在连续潜在空间中进行隐式推理和检索。实验表明，LatentRAG 在保持准确率的同时显著降低了延迟。

## 核心贡献

1. **潜在空间推理**：将 Agentic RAG 的自回归语言生成思维改为连续潜在空间中的隐式推理，消除显式子查询的延迟开销
2. **潜在检索机制**：在连续空间中进行检索，而非通过显式子查询访问外部知识库
3. **准确率-延迟帕累托最优**：在多个基准上实现与现有方法相当的准确率，同时将端到端延迟降低数倍

## 为什么重要

Agentic RAG 是记忆增强 LLM 智能体的核心技术范式——通过多步检索迭代利用外部记忆。但每次迭代生成自然语言思维和子查询的延迟是实际部署的瓶颈。LatentRAG 从根本上重新设计检索交互机制，将延迟降低到单步 RAG 的量级，同时保持多步推理能力。这对端侧部署的记忆系统尤为重要——移动设备上的记忆检索不能承受多次自回归生成的延迟。

## 与移动端/端侧的相关性

- **高相关性**：潜在空间推理避免了移动端 LLM 生成的长延迟，适合在手机/手表等设备上部署记忆检索
- **内存效率**：隐式推理不需要存储中间思维，降低峰值内存占用
- **端侧 RAG**：与 HeRo 等移动端 Agentic RAG 框架互补，可结合使用

## 参考文献

- 原论文: https://arxiv.org/abs/2605.06285
