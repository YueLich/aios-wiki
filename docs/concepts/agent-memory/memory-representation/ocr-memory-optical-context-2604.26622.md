---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory

**作者:** Jinze Li, Yang Zhang, Xin Yang, Jiayi Qu, Jinfeng Xu, Shuo Yang, Junhua Ding, Edith Cheuk-Han Ngai
**发表:** 2026-04-29
**备注:** Accepted to ACL 2026 (Main Conference)

## 摘要

Autonomous LLM agents increasingly operate in long-horizon, interactive settings where success depends on reusing experience accumulated over extended histories. However, existing agent memory systems are fundamentally constrained by text-context budgets: storing or revisiting raw trajectories is prohibitively token-expensive, while summarization and text-only retrieval trade token savings for information loss and fragmented evidence. To address this limitation, we propose Optical Context Retrieval Memory (OCR-Memory), a memory framework that leverages the visual modality as a high-density representation of agent experience, enabling retention of arbitrarily long histories with minimal prompt overhead at retrieval time. Specifically, OCR-Memory renders historical trajectories into images annotated with unique visual identifiers. OCR-Memory retrieves stored experience via a locate-and-transcribe paradigm that selects relevant regions through visual anchors and retrieves the corresponding verbatim text, avoiding free-form generation and reducing hallucination.

## 核心贡献

1. **视觉模态记忆编码**: 将历史轨迹渲染为带唯一视觉标识符的图像，以视觉方式存储agent经验，突破文本上下文预算限制
2. **locate-and-transcribe 检索范式**: 通过视觉锚点选择相关区域，检索对应原文，避免自由形式生成，减少幻觉
3. **任意长历史保持**: 光学编码使有效记忆容量大幅提升，同时保持检索时的忠实证据恢复
4. **幻觉减少**: 原文检索而非生成式摘要，避免了摘要引入的幻觉

## 为什么重要

在长时程Agent场景中，文本记忆面临 token 开销和信息丢失的双重困境。OCR-Memory 创新性地引入视觉模态作为记忆载体，利用图像的高信息密度突破文本瓶颈。ACL 2026 接收说明此方向获得顶级会议认可。

## 与端侧/移动端的相关性

OCR 图像编码比文本编码更紧凑，适合端侧资源受限环境。视觉锚点检索速度快，适合移动端实时场景。但图像渲染和 OCR 解码本身有计算开销，需要在具体硬件上验证。
