---
type: concept
tags: [sustainability, energy, privacy, on-device, trade-offs, system-design, 其他]
related: [[on-device-inference]], [[mobile-aios-overview]], [[edge-cloud-collaboration]]
sources:
  - url: https://arxiv.org/abs/2603.26603v1
    title: "Sustainability Is Not Linear: Quantifying Performance, Energy, and Privacy Trade-offs in On-Device Intelligence"
    date: 2026-03
created: 2026-04-14
---

# 可持续性不是线性的：端侧智能的性能-能耗-隐私权衡

## 概述

这篇论文量化分析了端侧 AI 系统中性能、能耗和隐私之间的非线性权衡关系。核心发现是：简单地「增加算力」并不能线性提升所有指标，三者之间存在复杂的耦合关系。

## 核心发现

- **性能-能耗**：模型精度提升 10% 可能需要 30% 的额外能耗
- **隐私-性能**：更强的隐私保护（如 [[gui-agent-privacy]] 中的本地处理）可能降低任务完成率
- **非线性拐点**：存在明显的效率拐点，超过后收益急剧下降

## 为什么重要

这对 [[mobile-aios-overview]] 的系统设计有深远影响。AIOS 不应只追求「更强的 AI」，而需要在三者间找到最优平衡点。不同厂商的策略（[[apple-intelligence]] 偏隐私、[[xiaomi-hyperai]] 偏性能）本质上是对这一权衡的不同取向。


## 核心问题

In this paper, we consider the problem of determining the density of monic polynomials over $\mathbb{Z}_p$ with squarefree discriminant over various subsets of the set of monic polynomials over $\mathbb{Z}_p$ of fixed degree. We compute the density of polynomials in each subset whose discriminant is squarefree, and we compute the density of polynomials $f$ in each subset such that $\mathbb{Z}_p[x]/(f(x))$ is the maximal order of $\mathbb{Q}_p[x]/(f(x))$.

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[edge-cloud-collaboration]] — 云端协同的能耗权衡
- [[on-device-inference]] — 端侧推理的能耗特点
- [[networking-energy-agentic]] — Agent 推理的网络能耗
