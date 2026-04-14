---
type: entity
tags: [on-device, music, ai-agent, iphone, personalization, mobile]
related: [[sense-less-infer-more]], [[mana-mobile-ad-detection]]
sources:
  - https://arxiv.org/abs/2604.10815v1
created: 2026-04-14
---

# MeloTune

## 概述
MeloTune 是一个部署在 iPhone 上的音乐 AI Agent，实现了 **Mesh Memory Protocol (MMP)** 和 **Symbolic-Vector Attention Fusion (SVAF)** 两个创新协议，用于主动式音乐推荐和情绪耦合。

## 核心技术
- **MMP（Mesh Memory Protocol）**：点对点记忆共享协议，允许多个设备上的 MeloTune 实例共享用户偏好和情绪状态
- **SVAF（Symbolic-Vector Attention Fusion）**：符号向量注意力融合，结合用户的唤醒度（arousal）学习进行个性化音乐编排
- **On-Device Arousal Learning**：端侧情绪唤醒度学习，无需云端推理

## 为什么重要
- 验证了**端侧 AI Agent** 可以在手机上完成复杂的情感理解和个性化推荐
- MMP 协议为多设备协同 AI Agent 提供了新范式
- 证明了 iPhone NPU 能力足以支持实时音乐情绪分析
- 与 [[sense-less-infer-more]] 的"少感知、多推理"理念相呼应——减少数据采集，更智能地推理用户意图

## 相关概念
- [[edge-inference]] — 端侧推理
- [[mobile-ai-agent]] — 移动端 AI Agent
