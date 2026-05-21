---
title: Scaling Long Video Understanding via Visual Memory Mechanism
arXiv: 2603.29252
date: 2026-03-31
tags: [agent-memory, multimodal-memory, visual-memory]
reviewer: auto
source: arXiv RSS/API
---

# Scaling Long Video Understanding via Visual Memory Mechanism

**arXiv**: 2603.29252 | **日期**: 2026-03-31 | **作者**: Tao Chen, Kun Zhang, Qiong Wu, Xiao Chen, Chao Chang, Xiaoshuai Sun, Yiyi Zhou, Rongrong Ji

## 摘要

FlexMem 从视觉记忆机制角度研究长视频理解问题，提出了一种新颖的无训练方法。核心思想是模拟人类观看视频的行为——持续观看视频内容并回忆与回答问题最相关的记忆片段。方法首先将视觉 KV 缓存作为记忆源，通过双路径压缩设计实现有效的记忆迁移和写入；同时探索了不同记忆读取策略以支持多样化的视频理解任务，包括流式视频理解。在单块 3090 GPU 上，FlexMem 可处理超过 1000 帧，在一些基准上达到与 GPT-4o 和 Gemini-1.5 Pro 相当甚至更好的性能。

## 核心贡献

1. **（参考文献待从原文补充）**

## 为什么重要

本文针对的是长程 Agent 的记忆系统关键挑战。与传统在离线场景设计的记忆方法不同，本文强调流式/在线视频理解中的实时记忆管理，对端侧 Agent 的实时视觉记忆有重要参考价值。

## 与端侧/移动端的相关性

- 视频流处理对端侧计算资源有严格限制，记忆压缩机制至关重要
- 轻量级视觉记忆管理对移动端/可穿戴设备上的视觉 Agent 有直接应用价值

## 参考文献

（参考文献待从原文补充）
