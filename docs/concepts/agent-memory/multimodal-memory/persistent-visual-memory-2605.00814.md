---
title: "Persistent Visual Memory: Sustaining Perception for Deep Generation in LVLMs"
arXiv: 2605.00814
date: 2026-05-01
authors: ["Siyuan Huang", "Xiaoye Qu", "Yafu Li", "Tong Zhu", "Zefeng He", "Muxin Fu", "Daizong Liu", "Wei-Long Zheng", "Yu Cheng"]
tags: [agent-memory, multimodal-memory, visual-memory, LVLM, attention-mechanism]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2605.00814
- **作者**: Siyuan Huang et al.
- **提交日期**: 2026-05-01
- **方向**: 视觉记忆 / 多模态 Agent / 长程生成

## 摘要（全文翻译）

虽然自回归大型视觉-语言模型（LVLM）在多模态任务中展示了卓越能力，但它们面临**"视觉信号稀释"**现象：文本历史的累积扩大了注意力分配函数，导致视觉注意力随生成序列长度**反比衰减**。

为对抗这一现象，本文提出 **Persistent Visual Memory (PVM)**，一个轻量级可学习模块，旨在确保持续、按需的视觉感知。作为 LVLM 中前馈网络（FFN）旁的并行分支，PVM 建立了**距离无关的检索路径**，直接为精确视觉感知提供视觉嵌入，从而从结构上缓解了深度生成固有的信号抑制。

在 Qwen3-VL 上的大量实验证明了 PVM 的有效性。

## 核心贡献

1. **视觉信号稀释问题的诊断**：文本历史累积导致视觉注意力衰减是 LVLM 的根本性问题
2. **PVM 模块**：可学习的并行视觉记忆分支，不依赖自回归解码器传递视觉信息
3. **距离无关检索**：视觉嵌入的检索路径绕过文本历史的长度依赖
4. **结构性解决**：而非调优干预，PVM 从架构层面缓解信号稀释

## 为什么重要

PVM 揭示了**多模态 Agent 在生成长文本时视觉感知退化的新问题**，并提出了一个优雅的架构解决方案。核心洞察：视觉信息和文本信息在自回归生成中竞争注意力资源，随着文本长度增加视觉信号被稀释。PVM 通过并行分支建立独立视觉检索路径来解决这个问题。

## 与端侧/移动端的相关性

PVM 的并行分支设计对**移动端多模态 Agent** 有参考价值。移动端的视觉-语言模型（如手机上的相机助手）需要在生成详细描述时保持对视觉输入的持续关注，PVM 提供了一种不需要额外推理步骤的持续感知方案。
