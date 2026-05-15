---
title: "InfoSFT: Learn More and Forget Less with Information-Aware Token Weighting"
arXiv: 2605.14967
date: 2026-05-14
tags: [agent-memory, continual-learning, fine-tuning, catastrophic-forgetting]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

监督微调（SFT）是利用离线专家演示教 LLM 新行为的标准方法。然而，标准 SFT 一致地拟合所有样本——包括在基础模型下低似然的样本——这会不成比例地将训练更新驱动到过拟合特定样本而非学习目标行为上。此外，适应这些低似然样本会诱导大的策略偏移，降低先验能力。现有方法通过过滤、再生或下加权低似然数据来缓解，但这样做往往恰好抑制了基础模型尚未学习的新行为。InfoSFT 提出了一种用于 SFT 目标的原则性加权方案，将学习信号集中在最大信息量、中等置信度的 tokens 上——即那些对基础模型既不过度熟悉也不会太不可能导致不稳定性的 tokens。只需对标准 token 级损失进行一行修改，InfoSFT 在数学、代码和思维链任务上跨多种模型家族显著提高泛化能力，同时更好地保留现有能力。

## 核心贡献

1. **信息感知 token 加权**：将学习信号集中在最大信息量、中等置信度的 tokens 上。
2. **防止知识遗忘**：避免过度下加权低似然数据而抑制新学习的知识。
3. **一行修改**：只需极小改动即可集成到现有 SFT 流程中。
4. **跨任务泛化改善**：在数学、代码、CoT 任务上均显著优于 vanilla SFT。
5. **保留先验能力**：比 likelihood-weighted 基线更好地保留预训练能力。

## 为什么重要

持续学习中的灾难性遗忘是一个核心挑战，InfoSFT 从 token 级 loss 角度提供了一种优雅的解决方案。该方法与记忆系统的持续学习高度相关——通过选择性地强化重要 tokens 来平衡新知识获取与旧知识保留。

## 与移动端/端侧的相关性

移动端 LLM 需要不断适应用户的个性化需求，InfoSFT 的 token 级加权方法计算开销小，适合端侧部署。对于需要持续微调的端侧应用场景（如个性化记忆更新），该方法具有直接应用价值。
