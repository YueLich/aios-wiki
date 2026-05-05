---
title: "Construction of Knowledge Graph based on Language Model"
arXiv: 2604.19137
date: 2026-04-21
tags: [agent-memory, memory-representation, knowledge-graph]
reviewer: auto
source: arXiv RSS/API
---

# Construction of Knowledge Graph based on Language Model

## 论文基本信息

- **作者**: Qiubai Zhu, Qingwang Wang, Haibin Yuan, Wei Chen, Tao Shen
- **机构**: （待补充）
- **arXiv**: https://arxiv.org/abs/2604.19137
- **代码**: （待补充）

## 核心贡献

1. **全面综述**: 提供 PLM/LLM 在知识图谱构建领域最新研究进展的全面综述。
2. **LLHKG 框架**: 提出基于轻量级 LLM 的超关系知识图谱（Hyper-Relational KG）构建框架 LLHKG。
3. **轻量级 LLM 的 KG 能力**: 证明轻量级 LLM 在 KG 构建能力上可与 GPT3.5 比肩。

## 研究背景与问题

知识图谱（KG）能有效整合海量数据中的有价值信息，在众多领域快速发展并广泛应用。但传统 KG 构建方法依赖人工标注，耗时耗力；基于深度学习的方案泛化能力弱。预训练语言模型（PLM）在 KG 构建领域展现出巨大潜力。

## 核心方法

### PLM 在 KG 构建中的作用
利用 PLM 的语言理解和生成能力，自动从文本数据中提取 KG 的关键信息：
- **实体识别**: 自动识别文本中的实体
- **关系抽取**: 自动抽取实体间关系

### LLHKG 框架
基于轻量级 LLM 的超关系知识图谱构建框架：
- 轻量级模型即可实现强大 KG 能力
- 可与 GPT3.5 相比较

## 为什么重要

这是知识图谱记忆表示方向的重要综述和实践工作。知识图谱作为记忆表示的核心形式之一，在 Agent 系统中扮演重要角色。LLHKG 证明了轻量级 LLM 也能有效构建 KG，对端侧知识图谱记忆系统有直接参考价值。

## 与移动端/端侧相关性

知识图谱是 Agent 记忆的重要表示形式之一。本文的 LLHKG 证明轻量级 LLM（可在端侧运行）也能有效构建和查询知识图谱，推动了端侧知识图谱记忆系统的可行性。
