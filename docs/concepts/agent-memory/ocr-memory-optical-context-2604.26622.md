---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
tags: [agent-memory, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory

## 论文基本信息

- **作者**: Jinze Li, Yang Zhang, Xin Yang, Jiayi Qu, Jinfeng Xu, Shuo Yang, Junhua Ding, Edith Cheuk-Han Ngai
- **arXiv**: https://arxiv.org/abs/2604.26622
- **领域**: cs.AI, cs.CL

## 摘要

自主 LLM Agent 在长程交互环境中运行，成功与否取决于对长期积累经验的复用。然而，现有 Agent 记忆系统受到文本上下文预算的根本约束：存储或回顾原始轨迹 token 成本过高，而摘要和纯文本检索在节省 token 的同时牺牲了信息完整性和证据的片段化。OCR-Memory 提出光学上下文检索记忆框架，利用视觉模态作为 Agent 经验的高密度表示，在检索时以极小 prompt 开销实现任意长度历史的保留。具体而言，OCR-Memory 将历史轨迹渲染为带有唯一视觉标识符的注释图像。OCR-Memory 通过"定位-转录"范式检索存储经验：通过视觉锚选择相关区域，检索对应原文，避免自由形式生成，减少幻觉。在长程 Agent 基准上的实验表明，在严格上下文限制下一致性提升，证明光学编码在保持忠实证据恢复的同时增加了有效记忆容量。

## 核心贡献

1. **Optical Memory Encoding**: 将 Agent 轨迹渲染为注释图像，实现高密度记忆存储
2. **Locate-and-Transcribe Retrieval**: "定位-转录"范式，视觉锚选择 + 原文检索
3. **Minimal Prompt Overhead**: 检索时极小 prompt 开销，支持任意长度历史
4. **Hallucination Reduction**: 原文检索而非生成，减少幻觉
5. **Long-horizon Benchmark**: 在长程 Agent 基准上一致性提升

## 研究背景与问题

纯文本记忆受限于 token 上下文预算：长轨迹存储 token 成本高，摘要牺牲信息完整性。视觉模态的信息密度远高于文本——一页图像可编码数千字内容。

## 核心方法

1. **Trajectory-to-Image Rendering**: 将 Agent 交互轨迹渲染为带视觉锚的注释图像
2. **Visual Anchor System**: 每段原文对应唯一视觉标识符
3. **Locate via Visual Matching**: 检索时通过视觉相似度匹配锚点
4. **Transcribe Original Text**: 锚点关联原文，无生成式幻觉
5. **Adaptive Resolution**: 根据上下文预算自适应图像分辨率

## 为什么重要

OCR-Memory 开创了用视觉模态解决 Agent 记忆 long-horizon 存储问题的先河。"定位-转录"范式避免了生成式检索的幻觉问题，对需要忠实回忆历史交互的 Agent 系统有重要价值。

## 与移动端/端侧相关性

1. **高密度记忆**: 视觉表示比文本 token 更紧凑，适合存储受限的移动端
2. **低延迟检索**: 图像匹配比 LLM 生成更快
3. **隐私保护**: 图像表示可本地存储和检索
4. **跨模态扩展**: 可结合摄像头实现所见即记忆
