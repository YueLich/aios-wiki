---
title: "Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability"
arXiv: 2604.21930
date: 2026-04-23
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# Temporal Taskification in Streaming Continual Learning: A Source of Evaluation Instability

**作者:** Nicolae Filat, Ahmed Hussain, Konstantinos Kalogiannis, Elena Burceanu  
**发表:** 2026-04-23

## 摘要

Streaming Continual Learning (CL) typically converts a continuous stream into a sequence of discrete tasks through temporal partitioning. We argue that this temporal taskification step is not a neutral preprocessing choice, but a structural component of evaluation: different valid splits of the same stream can induce different CL regimes and therefore different benchmark conclusions. To study this effect, we introduce a taskification-level framework based on plasticity and stability profiles, a profile distance between taskifications, and Boundary-Profile Sensitivity (BPS), which diagnoses how strongly small boundary perturbations alter the induced regime before any CL model is trained. We evaluate continual finetuning, Experience Replay, Elastic Weight Consolidation, and Learning without Forgetting on network traffic forecasting with CESNET-Timeseries24, keeping the stream, model, and training budget fixed while varying only the temporal taskification. Across 9-, 30-, and 44-day splits, we observe substantial changes in forecasting error, forgetting, and backward transfer, showing that taskification alone can materially affect CL evaluation. We further find that shorter taskifications induce noisier distribution-level patterns, larger structural distances, and higher BPS, indicating greater sensitivity to boundary perturbations. These results show that benchmark conclusions in streaming CL depend not only on the learner and the data stream, but also on how that stream is taskified, motivating temporal taskification as a first-class evaluation variable.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
