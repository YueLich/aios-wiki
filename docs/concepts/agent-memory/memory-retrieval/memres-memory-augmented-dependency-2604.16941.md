---
title: "MEMRES: A Memory-Augmented Resolver with Confidence Cascade for Agentic Python Dependency Resolution"
arXiv: "2604.16941"
date: "2026-04-18"
tags: [agent-memory, memory-retrieval, agentic-software, memory-augmented]
reviewer: auto
source: arXiv ti: search
---

# MEMRES: A Memory-Augmented Resolver with Confidence Cascade for Agentic Python Dependency Resolution

## 论文基本信息

- **arXiv ID**: 2604.16941
- **发表日期**: 2026-04-18
- **作者**: Dao Sy Duy Minh, Tran Chi Nguyen, Trung Kiet Huynh, Pham Phu Hoa, Nguyen Lam Phu Quy
- **类别**: cs.SE (Software Engineering)
- **来源**: arXiv ti: search

## 摘要

本文提出 **MEMRES**，一个用于 Python 依赖解决的智能体系统，引入多层置信级联机制，LLM 作为最后手段。MEMRES 整合了：
1. **自演化记忆（Self-Evolving Memory）**：通过技巧和捷径积累可复用的解决模式
2. **错误模式知识库（Error Pattern Knowledge Base）**：200+ 精心整理的 import-to-package 映射
3. **语义导入分析器（Semantic Import Analyzer）**
4. **Python 2 启发式检测器**：解决最大失败类别

在 HG2.9K 数据集上使用 Gemma-2 9B（10GB VRAM），MEMRES 解决了 2503/2890 个 snippet（86.6%，10次平均），远超 PLLM 的 54.7% 整体成功率。

## 核心贡献

1. **自演化记忆（Self-Evolving Memory）**：跨会话积累 Python 依赖解决模式，越用越准
2. **置信级联架构**：记忆检索 → 知识库查询 → 语义分析 → LLM 的分层决策链
3. **200+ 错误模式知识库**：覆盖常见 import-to-package 对，降低推理成本
4. **端侧友好设计**：仅需 10GB VRAM，适合边缘部署

## 为什么重要

MEMRES 代表了"记忆作为智能体能力放大器"的有效实践。与让 LLM 从零推理不同，MEMRES 将历史成功经验结构化存储，逐级降级至 LLM——这正是记忆系统应该做的事：**让简单问题用记忆解决，复杂问题才调用 LLM**。

## 与移动端/端侧的相关性

MEMRES 的端侧友好设计（10GB VRAM 可运行）和自演化记忆机制对移动端记忆系统有直接参考价值：
- **增量记忆积累**：设备上的个人助手可通过持续使用积累专属知识库
- **分级检索策略**：减少对云端 LLM 的依赖，提升响应速度和隐私保护
- **领域特定记忆**：针对移动端高频场景（日程、通讯、位置等）的专业化记忆模板

## 参考文献

（详见原论文）
