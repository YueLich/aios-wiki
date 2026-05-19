---
title: PyraVid: Hierarchical Multimodal Memory for Long-Horizon Video Reasoning
arXiv: 2605.17065
date: 2026-05-16
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv API
---

# PyraVid: Hierarchical Multimodal Memory for Long-Horizon Video Reasoning

## 论文信息

- **arXiv ID**: 2605.17065
- **发表日期**: 2026-05-16
- **作者**: Sikuan Yan, Sicheng Dong, Haotong Wang, Ercong Nie, Yilun Liu, Jinhe Bi, Yingjie Xu, Susanna Schwarzmann, Riccardo Trivisonno, Volker Tresp, Yunpu Ma
- **方向**: 多模态记忆

## 摘要

Memory has become an increasingly important component of agentic systems, as these systems are expected to reason over long-term experience. However, prior work has largely focused on unimodal memory, leaving multimodal memory relatively underexplored despite its central role in real-world applications. Compared with unimodal settings, multimodal memory introduces additional challenges, including heterogeneous input integration, person-centric information alignment, and evidence aggregation across different granularities. We present PyraVid, a hierarchical multimodal memory framework inspired by Event Segmentation Theory from cognitive science. PyraVid organizes long videos into a coarse-to-fine pyramid structure, enabling structured memory access and effective evidence aggregation. It further supports structure-guided memory expansion with pruning, allowing the retrieval of related events with strong causal connectivity but low semantic similarity while reducing noise. Experiments on multiple long-video understanding benchmarks show that PyraVid consistently improves performance across datasets, model scales, and question types, highlighting the effectiveness of hierarchical multimodal memory for long-horizon reasoning.

（摘要翻译：记忆已成为智能体系统的关键组件，因为这些系统需要长期经验中进行推理。然而，之前的工作主要关注单模态记忆，对多模态记忆的研究相对不足，尽管它在现实应用中扮演核心角色。与单模态设置相比，多模态记忆带来额外挑战，包括异构输入整合、以人为中心的信息对齐以及不同粒度下的证据聚合。PyraVid 是一个分层多模态记忆框架，受认知科学事件分割理论启发。PyraVid 将长视频组织为粗细粒度金字塔结构，实现结构化记忆访问和有效证据聚合。它进一步支持结构引导的记忆扩展与剪枝，允许检索因果关联强但语义相似度低的相关事件，同时减少噪声。在多个长视频理解基准上的实验表明，PyraVid 在数据集、模型规模和问题类型上均持续提升性能，突显了分层多模态记忆对长期推理的有效性。）

## 核心贡献

1. **事件分割理论启发的金字塔结构**：将长视频按 Event Segmentation Theory 分解为粗细粒度层次，支持从全局到局部的多尺度记忆访问。
2. **异构输入整合**：有效融合视觉、语言、音频等多模态信息，统一存储于分层记忆中。
3. **结构引导的记忆扩展与剪枝**：检索因果关联强但语义相似度低的相关事件，同时过滤噪声。
4. **跨粒度证据聚合**：在多个粒度上聚合证据，提升长视频问答的准确性。

## 为什么重要

多模态长视频理解是具身智能、监控系统、视频助手等应用的基础。传统方法依赖滑动窗口或全局注意，记忆能力有限。PyraVid 提出的分层多模态记忆为这类问题提供了可扩展的架构，对移动端/端侧部署尤其有价值——金字塔结构天然支持按需加载不同粒度的记忆层级，兼顾精度与效率。

## 与移动端/端侧的相关性

- 分层金字塔结构支持 lazy loading，适合资源受限的端侧设备
- 事件级记忆压缩减少长视频场景下的内存占用
- 模块化设计便于裁剪到移动端推理芯片

## 相关工作

- MEM: Multi-Scale Embodied Memory (2603.01455)
- CMMR-VLN: Vision-and-Language Navigation via Continual Multimodal Memory (2603.03596)
- VimRAG: Multimodal Memory Graph for Visual Context (2602.07624)
