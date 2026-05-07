---
title: HippoMM: Hippocampal-inspired Multimodal Memory for Long Audiovisual Event Understanding
arXiv: 2504.10739
date: 2025-04-14
tags: [agent-memory, multimodal-memory, episodic-memory, cognitive-modeling]
reviewer: auto
source: arXiv API
---

# HippoMM: Hippocampal-inspired Multimodal Memory for Long Audiovisual Event Understanding

## 摘要

理解长时 audiovisual 体验对计算系统仍是挑战，特别是与人类情景记忆相关的时间整合和跨模态关联。本文提出 HippoMM，一个受海马体启发的多模态记忆计算认知架构。HippoMM 不依赖规模扩展或架构复杂化，而是实现了三个集成组件：(i) 情景分割根据 audiovisual 输入变化切分视频；(ii) 记忆编码在分割片段上建立跨模态联合表征；(iii) 顺序上下文建模捕获事件的时间流。

## 核心贡献

1. **海马体启发的多模态记忆**：将神经科学的记忆机制映射为计算架构
2. **情景分割机制**：自动检测 audiovisual 输入变化切分记忆单元
3. **跨模态联合编码**：统一表示视觉和音频信息的记忆编码器
4. **时序上下文建模**：捕获事件的时间先后和因果关系
5. **无需超大规模模型**：在合理规模模型上实现长时理解

## 技术方法

### 情景分割 (Episodic Segmentation)
- 检测 audiovisual 信号的显著变化点
- 将连续体验切分为语义连贯的记忆片段
- 类似海马体的"事件分割"机制

### 跨模态记忆编码
- 将视频帧和对应音频编码为联合表征
- 保留关键视觉细节和音频事件
- 支持跨模态检索（用音频检索对应视觉记忆）

### 时序上下文建模
- 建立记忆片段之间的时间关系
- 支持时序推理（"A 事件发生在 B 之前"）
- 捕获因果关联（"因为 X 所以 Y"）

## 为什么重要

HippoMM 是"认知神经科学→Agent 记忆系统"桥梁的出色示例。海马体是人类情景记忆的关键结构，其计算机制（如情景分割、位置细胞）为 Agent 记忆系统提供了有生物学依据的设计原则。这对构建"像人一样记忆"的 Agent 有重要启发。

## 与移动端/端侧相关性

1. **AR/VR 记忆**：记录和回忆用户的沉浸式体验
2. **可穿戴设备**：处理连续的 audiovisual 输入流
3. **智能相机**：长时视频的自动情景分割和记忆构建
4. **认知辅助**：为认知障碍用户提供记忆辅助

## 参考文献

- Yueqian Lin, Jingyang Zhang, Qinsi Wang, Hancheng Ye. "HippoMM: Hippocampal-inspired Multimodal Memory for Long Audiovisual Event Understanding." arXiv:2504.10739, 2025.
