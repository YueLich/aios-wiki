---
title: "Bridging Modalities, Spanning Time: Structured Memory for Ultra-Long Agentic Video Reasoning"
arXiv: 2605.08271
date: 2026-05-08
tags: [agent-memory, multimodal-memory, video-reasoning]
reviewer: auto
source: arXiv API
---

## 摘要

理解超长视频（如 egocentric 记录、直播或跨越数天至数周的监控录像）仍是重大挑战。即使拥有百万 token 上下文窗口，当前多模态 LLM 的帧预算也仅能覆盖数十分钟的密集采样视频，大部分证据在推理开始前就被丢弃了。记忆增强和 Agent 化方法虽有帮助，但其检索在模态间碎片化，且缺乏跨越数天至数周的长程叙事摘要。本文提出 **MAGIC-Video**，一个无需训练的框架，围绕多模态记忆图（multimodal memory graph）和交织的叙事链（narrative chain）构建：图通过六种类型边统一情景记忆、语义记忆和视觉内容并支持跨模态检索；链则提取长程实体传记和重复活动事件。推理时，Agent 循环将图检索与叙事事实注入交织，同时覆盖超长视频的模态和时间维度。在 EgoLifeQA、Ego-R1 和 MM-Lifelong 上，MAGIC-Video 一致超越通用、长视频和 Agent 基线系统，在每个基准上比之前最好的 Agent 系统分别提升 10.1、7.4 和 5.9 分。

## 核心贡献

1. **多模态记忆图**：统一情景记忆、语义记忆和视觉内容，通过六种类型边连接，支持跨模态检索
2. **叙事链（NARRATIVE CHAIN）**：提取长程实体传记（entity biographies）和重复活动事件（recurring activity events）
3. **Agent 推理循环**：将图检索与叙事事实注入交织，同时覆盖超长视频的模态和时间维度
4. **无需训练**：完全基于现有组件的组合式设计，可与任意多模态 LLM 集成

## 为什么重要

超长视频理解是端侧智能（监控、穿戴设备、机器人）的核心场景。现有方法要么受限于上下文窗口（无法覆盖数天视频），要么检索碎片化（各模态独立检索缺乏统一视图）。MAGIC-Video 通过记忆图+叙事链的混合架构，首次实现了跨模态、跨时间的统一记忆检索，为长期视频分析提供了可扩展的解决方案。

## 与移动端/端侧相关性

- **穿戴设备 egocentric 视频**：MAGIC-Video 的 EgoLifeQA 基准直接对应第一人称视频记忆场景，是智能眼镜/AR 设备的潜在应用
- **轻量化设计**：无需训练、组合式架构，便于在端侧部署多模态记忆模块
- **长时间记忆**：叙事链提取的"实体传记"模式类似移动端的"人物/地点/活动"长期记忆组织方式
