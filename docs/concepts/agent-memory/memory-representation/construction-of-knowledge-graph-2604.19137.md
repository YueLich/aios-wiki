---
title: "Construction of Knowledge Graph based on Language Model"
arXiv: 2604.19137
date: 2026-04-21
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# Construction of Knowledge Graph based on Language Model

## 论文基本信息

- **作者**: ZhiQuan Chen, et al.
- **arXiv**: https://arxiv.org/abs/2604.19137
- **领域**: cs.KG, cs.CL

## 摘要

知识图谱能有效整合海量数据中的有价值信息，已在多个领域快速发展和广泛应用。传统知识图谱构建方法依赖人工标注，耗时耗力。基于深度学习的知识图谱构建方法泛化能力较弱。随着预训练语言模型的快速发展，PLM 在知识图谱构建领域展现出巨大潜力。论文全面综述了利用 PLM 自动从文本数据中提取关键信息（实体、关系）构建知识图谱的最新研究进展，并提出名为 LLHKG 的基于轻量级 LLM 的超关系知识图谱构建框架。

## 核心贡献

1. **PLM-based KG Survey**: 全面综述预训练语言模型在知识图谱构建中的应用
2. **LLHKG Framework**: 基于轻量级 LLM 的超关系知识图谱构建框架
3. **Entity & Relation Extraction**: 自动从文本中提取实体和关系
4. **Lightweight LLM 可比 GPT3.5**: 轻量级 LLM 达到 GPT3.5 水平的 KG 构建能力
5. **Generalization 提升**: 相比传统深度学习方法显著提升泛化能力

## 研究背景与问题

传统知识图谱构建依赖大量人工标注，深度学习方法泛化能力弱。PLM 的语言理解和生成能力为知识图谱构建提供了新范式。

## 核心方法

1. **PLM for Entity Extraction**: 利用 PLM 提取文本中的实体
2. **PLM for Relation Classification**: 利用 PLM 分类实体间关系
3. **LLM-based KG Generation**: 使用 LLM 生成知识图谱
4. **Hyper-relational KG**: 超关系知识图谱建模

## 为什么重要

该综述对 PLM 辅助知识图谱构建的全面总结，对构建 Agent 记忆系统的知识图谱层有重要参考价值。

## 与移动端/端侧相关性

1. **轻量级 LLM**: 移动端可运行轻量级 LLM 进行本地知识图谱构建
2. **离线 KG 构建**: 无需云端 API，本地完成知识图谱更新
3. **隐私保护**: 敏感文本数据不离开设备即可构建知识图谱
