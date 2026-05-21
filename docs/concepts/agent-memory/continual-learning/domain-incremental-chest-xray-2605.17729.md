---
title: "Domain Incremental Learning for Pandemic-Resilient Chest X-Ray Analysis"
arXiv: "2605.17729"
date: "2026-05-18"
tags: [continual-learning, domain-incremental, medical-imaging]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **标题**: Domain Incremental Learning for Pandemic-Resilient Chest X-Ray Analysis
- **arXiv ID**: 2605.17729
- **作者**: Danu Kim
- **发表日期**: 2026-05-18
- **方向**: Domain-Incremental Learning / Medical Imaging

## 核心贡献

1. **疫情韧性医学影像分析**: 针对胸部 X 光片的域增量持续学习方法，使模型能够持续适应跨医疗机构的成像差异，无需灾难性遗忘。
2. **类别感知平衡回放**: 提出类别感知平衡回放策略，在重放过程中维持类别分布平衡，防止少数类的性能退化。
3. **跨域泛化能力**: 在不同时期、不同设备的 Chest X-ray 数据上验证，证明模型能持续适应新的数据分布。

## 摘要

Deep learning models achieved high accuracy in pneumonia detection from chest X-rays. However, their generalization across clinical domains remains limited due to variations in imaging devices, acquisition protocols, and institutional conditions. This study introduces a replay-based domain-incremental continual learning designed to enable continual adaptation to cross-domain variations without catastrophic forgetting. The proposed method incorporates a class-aware balanced replay to maintain balanced performance across disease classes.

## 详细解读

### 研究背景

深度学习模型在胸部 X 光片肺炎检测上取得了高准确率，但在跨医疗机构部署时面临严峻挑战：
- 不同医院的成像设备差异（不同品牌、型号）
- 采集协议差异（辐射剂量、角度、分辨率）
- 机构间数据分布差异（患者人群差异）

### 核心方法

Domain-Incremental Learning 设置：
- 任务按时间顺序到来，每个任务对应一个新的医疗域
- 模型需要学习新域的同时保留旧域的知识
- 类别感知平衡回放：从旧域数据中选取样本重放，保持各疾病类别的平衡

## 为什么重要

疫情等突发事件会导致医疗数据的分布偏移（患者人群变化、检测标准变化）。持续适应能力对医疗 AI 系统至关重要，这篇论文提供了一个可行的技术方案。

## 与端侧/移动端的相关性

虽然这是医疗影像场景，但域增量学习方法对端侧个性化学习同样有意义：
- 端侧模型需要适应用户的个性化数据分布
- 类别平衡回放策略可用于处理用户数据中的类别不平衡问题
- 医疗 AI 的隐私约束（数据不能上传）与端侧持续学习天然契合

## 参考文献

（参考文献待从原文补充）
