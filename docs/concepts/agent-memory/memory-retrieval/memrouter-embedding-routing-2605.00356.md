---
title: "MemRouter: Memory-as-Embedding Routing for Long-Term Conversational Agents"
arXiv: 2605.00356
date: 2026-05-01
tags: [agent-memory, memory-retrieval, memory-write-decision]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Tianyu Hu, Weikai Lin, Weizhi Zhang, Jing Ma
- **提交日期**: 2026-05-01
- **方向**: 记忆写入决策 / 记忆路由

## 摘要

长期对话Agent必须决定哪些轮次应存储在外部记忆中，但近期系统依赖自回归LLM生成来做每轮决策。本文提出MemRouter，一个写入端记忆路由器，将记忆准入与下游回答主干解耦，用基于嵌入的路由策略替代逐轮记忆管理解码。

核心设计：MemRouter将每轮与近期上下文一起编码，通过冻结LLM的MLP头投影嵌入向量，生成记忆准入决策——无需为每轮调用解码完整的LLM。

## 核心贡献

1. **记忆准入与回答主干解耦**：将"是否记忆"决策从LLM生成过程中分离
2. **嵌入路由策略**：用MLP头投影替代自回归解码，决策效率高
3. **冻结LLM + MLP头**：无需额外训练记忆准入模型，复用预训练LLM能力
4. **显著降低写入开销**：消除逐轮LLM调用，延迟大幅下降

## 方法详解

**MemRouter架构**：
```
输入: [当前轮, 近期上下文] → LLM编码器 → 嵌入向量 → MLP头 → 记忆准入决策
                                           (冻结)     (训练)
```

**决策类型**：
- 记忆（Store in Memory）
- 丢弃（Discard）
- 更新（Update，合并到已有记忆）

**与现有方法对比**：
| 方法 | 每轮LLM调用 | 决策质量 | 延迟 |
|------|-----------|---------|------|
| LLM自回归解码 | 是 | 高 | 高 |
| 简单启发式 | 否 | 低 | 低 |
| MemRouter | 否 | 高 | 低 |

## 为什么重要

记忆写入决策是记忆系统的关键瓶颈——传统方法需要为每轮调用LLM做决策，开销巨大。MemRouter通过嵌入路由将这个过程压缩为单次前向传播，为端侧实时记忆管理开辟了新路径。

## 与端侧/移动端的相关性

- **高度端侧相关**：消除逐轮LLM调用，移动设备可本地运行
- MLP头轻量，可在CPU上高效推理
- 冻结LLM + 轻量MLP头的设计适合移动端部署
- 个人助手的长期记忆管理（联系人偏好、历史交互）
