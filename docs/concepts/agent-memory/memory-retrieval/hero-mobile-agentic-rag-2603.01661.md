---
title: "HeRo: Adaptive Orchestration of Agentic RAG on Heterogeneous Mobile SoC"
arXiv: 2603.01661
date: 2026-03-02
tags: [agent-memory, memory-retrieval, mobile, edge, agentic-rag]
reviewer: auto
source: arXiv RSS/API
---

# HeRo: Adaptive Orchestration of Agentic RAG on Heterogeneous Mobile SoC

## 论文基本信息

- **标题**: HeRo: Adaptive Orchestration of Agentic RAG on Heterogeneous Mobile SoC
- **arXiv ID**: 2603.01661
- **发表日期**: 2026-03-02
- **作者**: Maoliang Li, Jiayu Chen, Zihao Zheng, Ziqian Li, Xinhao Sun, Guojie Luo, Chenchen Liu, Xiang Chen
- **方向**: 记忆检索 · 移动端 · Agentic RAG
- **类别**: cs.DC

## 摘要（原文翻译）

随着移动设备计算能力的提升，在异构系统芯片（SoC）上本地部署 Agentic 检索增强生成（RAG）已成为增强 LLM 应用的有前景途径。然而，Agentic RAG 引入了多阶段工作流与异构模型及动态执行流，而移动 SoC 表现出强加速器亲和性、形状敏感性和共享内存带宽竞争，使得朴素调度失效。本文提出 HeRo，一个用于移动 SoC 低延迟 Agentic RAG 的异构感知框架。HeRo 为每个子阶段和模型-PU 配置构建基于性能分析的模型，捕捉延迟、工作负载形状和竞争引起的减速，并在轻量级在线调度器中利用它们，实现多阶段流水线的高效协同调度。

## 核心贡献

1. **异构感知调度**：为移动 SoC 的 CPU/GPU/NPU 异构计算资源建立性能模型
2. **竞争感知建模**：捕捉共享内存带宽竞争对推理延迟的影响
3. **轻量级在线调度**：HeRo 的调度器开销极低，适合实时场景
4. **跨 SoC 通用性**：框架可迁移到不同移动 SoC 架构

## 为什么重要

移动端是 Agent Memory 最重要的落地场景——用户的个人记忆（照片、位置、行为历史）高度敏感，不应上传云端。HeRo 解决了 Agentic RAG 在移动端部署的核心挑战：多阶段工作流（检索→重排→生成）的动态调度。移动 SoC 的异构性（CPU 处理检索、GPU 处理生成、NPU 处理嵌入）使得朴素串行调度效率极低。HeRo 通过性能建模和在线调度最大化并行度，是记忆系统端侧部署的重要基础设施。

## 与移动端/端侧的相关性

- **极高相关性**：直接解决 Agentic RAG 在手机/手表等设备上的部署问题
- **低延迟**：对需要实时响应的记忆系统（如 AR 辅助）至关重要
- **隐私保护**：本地部署意味着用户记忆数据不离开设备
- **异构计算**：充分利用移动 SoC 的 CPU/GPU/NPU 协同

## 参考文献

- 原论文: https://arxiv.org/abs/2603.01661
