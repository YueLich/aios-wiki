---
title: "Towards Autonomous Memory Agents"
arXiv: "2602.22406"
date: "2026-02-25"
tags: [agent-memory, memory-retrieval, autonomous-agents]
reviewer: auto
source: arXiv API
---

## 论文概述

**核心问题**：现有记忆代理是**被动响应**的——记忆增长受限于恰好可用的信息，记忆代理很少在不确定时主动寻求外部输入。

**解决思路**：提出**自主记忆代理**（Autonomous Memory Agents），能以最小成本主动获取、验证和整理知识。U-Mem 是这一理念的具体实现。

## 核心贡献

1. **成本感知知识提取级联**（Cost-Aware Knowledge-Extraction Cascade）
   - 从廉价 self/teacher 信号逐级升级到工具验证的研究，仅在必要时寻求专家反馈

2. **语义感知 Thompson 采样**
   - 平衡记忆的探索与利用，缓解冷启动偏差

3. **SOTA 性能**：在 HotpotQA（Qwen2.5-7B）上提升 14.6 分，AIME25（Gemini-2.5-flash）上提升 7.33 分，超越 RL 基优化方法

## 为什么重要

- 首次将**主动知识获取**引入记忆代理，记忆增长不再受限于"恰好可用"
- 成本感知的设计适合真实部署场景

## 与端侧/移动端相关性

1. **成本感知设计**：级联式获取策略天然适合端侧的带宽/计算资源受限场景
2. **无需训练**：基于 LLM 的知识提取和 Thompson 采样，可在轻量模型上运行
