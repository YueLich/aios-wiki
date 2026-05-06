---
title: "Fine-Tuning Regimes Define Distinct Continual Learning Problems"
arXiv: 2604.21927
date: 2026-04-25
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Fine-Tuning Regimes Define Distinct Continual Learning Problems

## 论文基本信息

- **作者**: Paul-Tiberiu Iordache, Elena Burceanu
- **arXiv**: https://arxiv.org/abs/2604.21927
- **领域**: cs.LG, cs.AI

## 摘要

持续学习（CL）研究模型如何在保留已有知识的同时顺序获取新任务。尽管 CL 方法评测取得了实质性进展，但比较评估通常固定微调策略（fine-tuning regime）。论文认为微调策略——由可训练参数子空间定义——本身是一个关键评估变量。论文形式化了这一概念，证明不同的微调策略定义本质上不同的 CL 问题，当前基准评估忽视这一点导致了不公平比较。

## 核心贡献

1. **Fine-tuning Regime 形式化**: 首次将微调策略形式化为 CL 评估的关键变量
2. **Distinct CL Problems**: 证明不同微调策略定义本质上不同的 CL 问题
3. **Regime-aware Benchmarking**: 提出考虑微调策略的公平基准评估方法
4. **Method × Regime Interaction**: 分析 CL 方法与微调策略的交互效应
5. **实践建议**: 为不同微调资源场景选择合适 CL 方法提供指导

## 研究背景与问题

当前 CL 基准评估假设一个固定的微调策略（通常是全量微调），但实际部署中可用的微调资源差异巨大。忽略这一变量导致方法比较不公平。

## 核心方法

1. **Fine-tuning Regime Taxonomy**: 系统分类不同类型的微调策略（full/partial/adapter/prefix）
2. **Regime-specific Evaluation**: 在多种微调策略下评估 CL 方法
3. **Interaction Analysis**: 分析方法与策略的交互效应
4. **Resource-aware Recommendation**: 根据可用微调资源推荐合适的方法

## 为什么重要

该研究揭示了 CL 评估中一个被忽视的关键变量，推动了更公平的 CL 方法比较。对 Agent 系统，这意味着选择 CL 方法时必须考虑可用的微调资源。

## 与移动端/端侧相关性

1. **移动端微调限制**: 移动端 Agent 通常只能做轻量级微调（如 adapter、prefix）
2. **资源感知方法选择**: 根据设备能力选择合适的 CL 方法
3. **联邦学习场景**: 联邦设置下只能做有限本地微调
