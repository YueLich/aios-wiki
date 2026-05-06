---
title: "MELODI: Exploring Memory Compression for Long Contexts"
arXiv: 2410.03156
date: 2024-10-04
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# MELODI: Exploring Memory Compression for Long Contexts

## 论文基本信息

- **作者**: Yinpeng Chen, DeLesley Hutchins, Aren Jansen
- **arXiv**: https://arxiv.org/abs/2410.03156
- **领域**: cs.CL, cs.AI

## 摘要

MELODI 提出一种分层记忆压缩架构，用于在短上下文窗口中处理长文档。核心思想是将短期记忆和长期记忆表示为跨网络层和上下文窗口的分层压缩方案。短期记忆通过跨多个窗口的递归压缩实现，长期记忆通过跨网络层的分层压缩维护。在长文档问答和摘要任务上，MELODI 在保持 95% 性能的同时，将推理时的上下文长度减少 70%。

## 核心贡献

1. **Hierarchical Memory Compression**: 跨层和跨窗口的分层记忆压缩方案
2. **70% Context Reduction**: 在保持 95% 任务性能下减少 70% 上下文长度
3. **Long Document QA/Summarization**: 在长文档任务上验证有效性
4. **Recursive Short-term Memory**: 短期记忆通过递归压缩跨多个窗口维护
5. **Layer-wise Long-term Memory**: 长期记忆跨网络层压缩，保留高层语义

## 研究背景与问题

Transformer 的上下文窗口限制了 LLM 处理长文档的能力。现有方法（稀疏注意力、滑动窗口）会丢失重要的跨窗口依赖关系。MELODI 旨在用分层压缩表示替代简单的上下文截断，保持跨依赖关系的同时减少实际输入 token。

## 核心方法

1. **Recursive Context Compression**: 每个新窗口到来时，将当前窗口压缩并与下一窗口递归合并
2. **Layer-wise Memory Hierarchy**: 在网络不同层维护不同粒度的记忆（浅层=细节，深层=语义）
3. **Compression Module**: 可学习的压缩模块，比手工设计的摘要更保留关键信息
4. **Retrieval-augmented Decompression**: 检索时通过增强解码恢复被压缩的细节
5. **Long-document Benchmark**: 构建长文档记忆压缩基准，包含多文档推理任务

## 为什么重要

MELODI 的分层压缩思想对 Agent 记忆系统有重要启示：不是所有记忆都同等重要，不同层级的网络关注不同粒度的信息。借鉴这一思想，可以设计更高效的 Agent 记忆架构。

## 与移动端/端侧相关性

1. **70% 上下文减少**: 对移动端有限的上下文窗口有直接价值
2. **分层设计**: 可在移动端部署不同层级的记忆模块，实现资源aware的记忆管理
3. **长文档处理**: 适合手机文档助手、长对话历史总结等移动场景
4. **压缩模块可学习**: 比固定压缩策略更灵活，可适应不同任务
