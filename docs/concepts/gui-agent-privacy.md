---
type: concept
tags: [privacy, gui-agent, personalization, mobile, preference-optimization]
related: [[mobile-agent-framework]], [[pspa-bench-gui-agent]], [[sustainability-ondevice-intelligence]]
sources:
  - url: https://arxiv.org/abs/2604.11259v1
    title: "Mobile GUI Agent Privacy Personalization with Trajectory Induced Preference Optimization"
    date: 2026-04
created: 2026-04-14
---

# 移动 GUI Agent 的隐私保护个性化

## 概述

这篇论文提出了一种在保护隐私的前提下实现移动 GUI Agent 个性化的方法，使用轨迹诱导的偏好优化（Trajectory Induced Preference Optimization）。

## 核心问题

Agent 个性化需要学习用户行为，但这涉及隐私敏感数据：
- 操作序列暴露用户的 App 使用习惯
- 偏好数据可能泄露个人兴趣
- 云端学习带来数据外泄风险

## 技术方向

- **轨迹诱导**：从操作轨迹中提取抽象偏好模式
- **本地优化**：所有学习在端侧完成
- **偏好优化**：DPO 类方法适配 Agent 场景

## 为什么重要

这是 [[mobile-agent-framework]] 落地的关键瓶颈。[[apple-intelligence]] 的「隐私优先」理念需要这类技术支撑——Agent 越智能，收集的数据越敏感。与 [[sustainability-ondevice-intelligence]] 的隐私-性能权衡分析相呼应。

## 关联

- [[pspa-bench-gui-agent]] — 个性化评测基准
- [[secagent-mobile-gui]] — 语义上下文理解
- [[lcsb-finetuning-ondevice]] — 端侧学习技术
