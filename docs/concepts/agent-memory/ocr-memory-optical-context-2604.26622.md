---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
authors: ["Jinze Li", "Yang Zhang", "Xin Yang", "Jiayi Qu", "Jinfeng Xu", "Shuo Yang", "Junhua Ding", "Edith Cheuk-Han Ngai"]
tags: [agent-memory, memory-representation, multimodal-memory]
reviewer: auto
source: arXiv API
---

## 摘要

OCR-Memory 针对长期交互式 Agent 记忆系统的文本上下文预算限制问题，提出利用视觉模态作为 Agent 经验的高密度表示。通过将历史轨迹渲染为带唯一视觉标识符的图像，实现任意长历史的保留，最小化检索时的提示开销。采用"定位-转录"（locate-and-transcribe）范式，通过视觉锚点选择相关区域并检索对应文本。

## 背景问题

现有 Agent 记忆系统受制于文本上下文预算（token budget）：
- 存储或回顾原始轨迹的 Token 成本过高
- 摘要和纯文本检索虽节省 Token，但造成信息丢失和证据碎片化

## 核心方法

1. **视觉轨迹渲染**：将历史轨迹渲染为带唯一视觉标识符的图像
2. **OCR 检索范式**：定位-转录（locate-and-transcribe）
   - 通过视觉锚点选择相关区域
   - 检索对应文本内容
3. **最小化提示开销**：视觉表示实现任意长历史保留

## 核心贡献

1. 提出视觉模态作为 Agent 经验的高密度表示
2. OCR-Memory 框架：突破文本上下文预算限制
3. "定位-转录"检索范式，平衡存储效率与信息完整性
4. 支持任意长度历史的保留

## 为什么重要

长期交互式 Agent（如个人助手、自动化工作流）需要跨越大量交互历史。当轨迹长度超过 LLM 上下文窗口时，传统方法必须在压缩（信息损失）和截断（历史断裂）之间取舍。OCR-Memory 通过视觉模态的高信息密度，在保持检索质量的同时大幅降低 Token 消耗，为端侧 Agent 提供了可行的长程记忆方案。

## 端侧相关性

- 视觉记忆压缩率远高于文本，适合资源受限的端侧设备
- 减少 Token 消耗意味着更低的推理成本和更快的响应速度
- 可与本地视觉模型结合实现端侧 OCR 检索
