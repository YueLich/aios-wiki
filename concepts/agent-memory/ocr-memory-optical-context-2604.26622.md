---
title: "OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory"
arXiv: 2604.26622
date: 2026-04-29
tags: [agent-memory, memory-retrieval, multimodal, vision]
reviewer: auto
source: arXiv RSS/API
---

# OCR-Memory: Optical Context Retrieval for Long-Horizon Agent Memory

## 论文基本信息

- **arXiv ID**: 2604.26622
- **作者**: Jinze Li, Yang Zhang, Xin Yang, Jiayi Qu, Jinfeng Xu
- **提交日期**: 2026-04-29
- **类别**: cs.CL

## 摘要

自主 LLM Agent 在长时程、交互式环境中运行，其成功越来越依赖对长期积累经验的复用。然而现有 Agent 记忆系统在文本上下文预算上受到根本性约束：存储或回溯原始轨迹成本极高（token 消耗大），而摘要压缩和纯文本检索虽然节省 token 但带来信息损失和碎片化证据问题。为解决这一局限，本文提出 OCR-Memory（Optical Context Retrieval Memory），利用视觉模态作为 Agent 经验的高密度表示，以极少的 prompt 开销保留任意长度历史，并在检索时实现高效复用。具体而言，OCR-Memory 将历史轨迹渲染为带有唯一视觉标识符的图像，通过「定位-转录」（locate-and-transcribe）范式检索——通过视觉锚点选择相关区域，再检索对应文本。

## 核心贡献

1. **视觉模态高密度表示**：将 Agent 历史轨迹渲染为带视觉标识的图像，相比纯文本大幅压缩存储体积。
2. **定位-转录检索范式**：通过视觉锚点精确定位记忆区域，避免全文 token 扫描。
3. **极低检索开销**：图像表示 + 视觉锚点使检索 prompt 开销与历史长度解耦。
4. **实验验证**：在长时程交互任务上验证了 OCR-Memory 的有效性。

## 为什么重要

这是首个将视觉表示引入 Agent 记忆系统的研究，解决了长时程 Agent 的 token 预算瓶颈。传统文本记忆在超长对话中面临「存储不起、摘要不准」的两难，OCR-Memory 通过跨模态压缩提供了第三条路。这对移动端 Agent 尤其有意义——移动设备上 App 界面的屏幕截图本身就是视觉信息，OCR-Memory 与移动端 UI Agent 高度契合。

## 与移动端/端侧相关性

- 移动端 UI Agent 天然产生大量屏幕截图，OCR-Memory 可直接利用这些视觉信息作为记忆载体
- 移动端设备存储受限，视觉压缩表示相比文本 token 更高效
- Apple 屏幕识别、Android UI 层次结构等都已有成熟 OCR 工具，与 OCR-Memory 范式兼容
