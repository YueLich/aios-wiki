---
type: concept
tags: [energy, agent, inference, survey, networking, efficiency]
related: [[sustainability-ondevice-intelligence]], [[edge-cloud-offloading]], [[mobile-agent-framework]]
sources:
  - url: https://arxiv.org/abs/2604.07857v1
    title: "Networking-Aware Energy Efficiency in Agentic AI Inference: A Survey"
    date: 2026-04
created: 2026-04-14
---

# Agent AI 推理中的网络感知能效：综述

## 概述

这是一篇关于 Agent AI 推理中能效问题的综述，特别关注了网络通信开销对整体能耗的影响。

## 核心观点

Agent 系统的能耗不仅是模型推理本身：
- **网络开销**：Agent 与云端、工具 API 的通信消耗显著
- **频繁交互**：Agent 的多步规划导致大量 API 调用
- **端云混合**：本地和云端计算的能耗特性差异巨大

## 为什么重要

这是 [[sustainability-ondevice-intelligence]] 的重要延伸。现有能效研究主要关注模型推理本身，但 Agent 系统的特殊性在于其频繁的外部交互。对于 [[mobile-aios-overview]] 中 Agent 层的设计，需要从整体系统角度考虑能效。


## 核心问题

This paper presents a comprehensive framework for transaction posting and pricing in Layer 2 (L2) blockchain systems, focusing on challenges stemming from fluctuating Layer 1 (L1) gas fees and the congestion issues within L2 networks. Existing methods have focused on the problem of optimal posting strategies to L1 in isolation, without simultaneously considering the L2 fee mechanism. In contrast, our work offers a unified approach that addresses the complex interplay between transaction queue dynamics, L1 cost variability, and user responses to L2 fees. We contribute by (1) formulating a dynamic model that integrates both posting and pricing strategies, capturing the interplay between L1 gas price fluctuations and L2 queue management, (2) deriving an optimal threshold-based posting policy 

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[edge-cloud-offloading]] — 端云协同架构
- [[mobile-agent-framework]] — Agent 系统设计
- [[sustainability-ondevice-intelligence]] — 能耗权衡分析
