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
- **作者**: Jingyi Peng, Zhongwei Wan, Weiting Liu
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

1. **PRISM 框架**：联合检索-压缩，解决准确率与效率的权衡
2. **四组件正交设计**：分层搜索 + 意图感知成本 + 证据压缩 + 自适应路由
3. **零微调**：无需训练或修改上游摄入流程，部署友好
4. **Pareto 最优**：占据准确率-上下文-成本前沿的空缺区域

## 为什么重要

记忆检索的核心矛盾是：全面检索成本高、经济检索质量差。PRISM 通过解耦检索（结构化图遍历）和压缩（LLM 端），在严格上下文预算下实现高效高质量答案。

## 与移动端/端侧相关性

- 端侧智能体需要在有限上下文窗口内做记忆检索
- 零微调、推理时组件设计，适合资源受限的端侧部署
- 自适应路由让简单查询绕过 LLM，降低端侧计算负载

## 参考文献

- 原文: https://arxiv.org/abs/2605.12260
