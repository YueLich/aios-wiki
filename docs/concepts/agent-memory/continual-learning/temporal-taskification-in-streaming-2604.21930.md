---
title: "Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability"
arXiv: 2604.21930
date: 2026-04-23
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability

## 论文基本信息

- **作者**: Nicolae Filat, Ahmed Hussain, Konstantinos Kalogiannis, Elena Burceanu
- **arXiv**: https://arxiv.org/abs/2604.21930
- **领域**: cs.LG
- **备注**: 12 pages, 2 figures

## 摘要

Streaming Continual Learning (CL) typically converts a continuous stream into a sequence of discrete tasks through temporal partitioning. We argue that this temporal taskification step is not a neutral preprocessing choice, but a structural component of evaluation: different valid splits of the same stream can induce different CL regimes and therefore different benchmark conclusions. To study this effect, we introduce a taskification-level framework based on plasticity and stability profiles, a profile distance between taskifications, and Boundary-Profile Sensitivity (BPS), which diagnoses how strongly small boundary perturbations alter the induced regime before any CL model is trained. We evaluate continual finetuning, Experience Replay, Elastic Weight Consolidation, and Learning without Forgetting on network traffic forecasting with CESNET-Timeseries24, keeping the stream, model, and training budget fixed while varying only the temporal taskification. Across 9-, 30-, and 44-day splits, we observe substantial changes in forecasting error, forgetting, and backward transfer, showing that taskification alone can materially affect CL evaluation. We further find that shorter taskifications induce noisier distribution-level patterns, larger structural distances, and higher BPS, indicating greater sensitivity to boundary perturbations. These results show that benchmark conclusions in streaming CL depend not only on the learner and the data stream, but also on how that stream is taskified, motivating temporal taskification as a first-class evaluation variable.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
