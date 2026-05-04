---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
authors: ["Jinze Li", "Yang Zhang", "Xin Yang", "Jiayi Qu", "Jinfeng Xu", "Shuo Yang", "Junhua Ding", "Edith Cheuk-Han Ngai"]
tags: [agent-memory, memory-representation, visual-memory, trajectory-memory, long-horizon]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.26622
- **作者**: Jinze Li et al.
- **提交日期**: 2026-04-29
- **方向**: 视觉记忆表示 / 轨迹记忆 / 长程 Agent

## 摘要（全文翻译）

自主 LLM Agent 越来越多地在**长程、交互式环境**中运作，其成功依赖于重用长期积累的经验。然而，现有 Agent 记忆系统从根本上受制于**文本上下文预算**：存储或回访原始轨迹的 token 成本高得令人望而却步，而摘要和纯文本检索虽然节省 token，但以信息损失和碎片化证据为代价。

本文提出 **OCR-Memory**（Optical Context Retrieval Memory），一种利用**视觉模态**作为 Agent 经验高密度表示的记忆框架，在检索时以最小提示开销保留任意长度的历史。具体而言，OCR-Memory 将历史轨迹**渲染为图像**，用视觉编码器支持高效的上下文检索。

## 核心贡献

1. **视觉模态作为记忆表示**：将文本/轨迹信息渲染为图像，利用视觉的高信息密度绕过 token 预算限制
2. **OCR-Memory 框架**：无需详细阅读文本即可通过视觉编码器快速检索相关历史
3. **极低检索开销**：检索时只需处理图像嵌入，而非重建完整文本轨迹
4. **任意长度历史保留**：视觉表示允许保留完整历史而不受 token 预算限制

## 为什么重要

这是第一个**将视觉渲染引入 Agent 记忆系统**的论文。核心洞察：视觉信息密度远高于文本（一个图像可以编码数千个 token 的空间/时序关系），而视觉编码器的检索成本远低于重建文本。OCR-Memory 解决了一个根本矛盾：Agent 需要保留完整历史经验，但完整文本的 token 成本无法承受。

## 与端侧/移动端的相关性

**高度相关**。移动端 Agent 的上下文窗口极为有限，OCR-Memory 的视觉压缩方案可以在保持完整历史信息的同时大幅减少 token 使用。未来的移动端记忆系统可以将用户交互轨迹渲染为紧凑的视觉表示，通过图像嵌入快速检索相关经验。
