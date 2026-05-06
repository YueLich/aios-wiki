---
title: "IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory"
arXiv: 2604.20136
date: 2026-04-22
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

# IMPACT-CYCLE: A Contract-Based Multi-Agent System for Claim-Level Supervisory Correction of Long-Video Semantic Memory

## 论文基本信息

- **作者**: Weitong Kong, Di Wen, Kunyu Peng, David Schneider 等
- **arXiv**: https://arxiv.org/abs/2604.20136
- **代码**: https://github.com/MKong17/IMPACT_CYCLE

## 摘要

长视频理解中的纠错代价高昂：现有 multimodal 流程产生不透明的整体输出，无法检查中间状态，迫使标注者从原始视频重建时间逻辑。核心瓶颈不仅是生成质量，还在于缺乏监督界面使人力投入与错误范围成比例。IMPACT-CYCLE 将长视频理解重新定义为基于共享语义记忆的迭代声明级维护——结构化版本化状态编码类型化声明、声明依赖图和来源日志。在权限合约下运作的角色专业化 Agent 将验证分解为局部对象关系正确性、跨时间一致性和全局语义连贯性，修正局限于结构依赖的声明。当自动证据不足时，系统升级到人工仲裁作为最高权限；依赖闭包重验证确保修正代价与错误范围成比例。实验在 VidOR 上展示了下游推理的实质性改进（VQA: 0.71 → 0.79）和 4.8 倍人工仲裁代价降低。

## 核心贡献

1. **Claim-level Semantic Memory**: 以类型化声明和依赖图管理长视频语义记忆
2. **Contract-based Multi-Agent**: 权限合约下的角色专业化 Agent 协作
3. **4.8x Cost Reduction**: 4.8 倍人工仲裁代价降低
4. **Proportional Error Correction**: 修正代价与错误范围成比例
5. **VQA 0.71 → 0.79**: 下游推理实质性改进

## 研究背景与问题

长视频理解中错误修正代价极高，因为需要从原始视频重建时间逻辑。传统 pipeline 无法检查中间状态，人工纠错必须从零开始。

## 核心方法

1. **Semantic Memory State**: 结构化版本化记忆，编码声明、依赖图、来源日志
2. **Role-specialized Agents**: 局部正确性、跨时间一致性、全局连贯性三个角色
3. **Authority Contract**: 显式权限合约定义 Agent 的决策边界
4. **Human Escalation**: 自动证据不足时升级到人工仲裁
5. **Dependency-closure Re-verification**: 依赖闭包重验证确保修正代价可控

## 为什么重要

IMPACT-CYCLE 展示了如何在多 Agent 系统中维护共享语义记忆，并实现高效的人机协作修正。这对需要长视频理解的 Agent 系统（如视频助手、监控系统）有直接价值。

## 与移动端/端侧相关性

1. **端侧视频理解**: 移动端视频分析需要有效的记忆和修正机制
2. **计算资源受限**: 修正代价与错误范围成比例，适合资源受限场景
3. **多 Agent 协作**: 移动端多 Agent 系统协调的参考架构
4. **长视频处理**: 突破移动端上下文窗口限制的长视频处理方案
