---
title: "Exploring Multimodal LMMs for Online Episodic Memory Question Answering on the Edge"
arXiv: "2602.22455"
date: "2026-02-25"
tags: [agent-memory, multimodal-memory, edge, episodic-memory, wearable]
reviewer: auto
source: arXiv RSS/API
---

# Exploring Multimodal LMMs for Online Episodic Memory Question Answering on the Edge

## 论文基本信息

- **arXiv ID**: 2602.22455
- **发表日期**: 2026-02-25
- **作者**: Giuseppe Lando, Rosario Forte, Antonino Furnari
- **方向**: Multimodal Memory, Edge AI, Episodic Memory, Wearable Computing
- **类别**: cs.CV

## 摘要

可穿戴助手的云端卸载方案存在隐私和延迟问题，本文研究在边缘设备上使用多模态大语言模型（MLLMs）进行实时在线情景记忆问答的可行性。将问答流程整合为两个异步线程：Descriptor Thread 持续将视频转换为轻量级文本记忆；QA Thread 基于文本记忆进行推理回答。在 QAEgo4D-Closed 基准上的实验表明：消费级 8GB GPU 端侧配置达到 51.76% 准确率，首 token 延迟（TTFT）0.41 秒；本地企业级服务器配置达到 54.40% 准确率，TTFT 0.88 秒；云端方案准确率为 56.00%。边缘方案的性能具有竞争力，证明了隐私保护的端侧情景记忆检索的可行性。

## 核心贡献

### 1. 边缘优先的多模态记忆问答架构

针对可穿戴助手的隐私和延迟约束，采用端侧优先设计：
- **Descriptor Thread**：持续将视频流转换为轻量级文本记忆（不是直接存储视频，而是提取文字描述），大幅降低存储和计算开销
- **QA Thread**：基于文本记忆进行问答推理，两个线程异步协作

### 2. 严格资源约束下的性能分析

在多种硬件配置上系统评估了性能-延迟权衡：
- **消费级 8GB GPU**：51.76% 准确率，TTFT 0.41 秒 — 适合日常可穿戴场景
- **本地企业级服务器**：54.40% 准确率，TTFT 0.88 秒 — 适合本地智能家居场景
- **云端方案**：56.00% 准确率 — 作为对照

### 3. 隐私保护的端侧方案

端侧方案在准确率上仅落后云端 4-5%，但完全避免了数据外传，对于健康监测、日常记录等敏感场景具有重要价值。

### 4. 视频到文本的记忆压缩

将视频流转换为轻量级文本记忆是关键设计 — 避免了视频的直接存储和传输，在保护隐私的同时保留了足够的语义信息用于问答。

## 为什么重要

这是首批系统研究边缘设备上多模态情景记忆问答的论文之一。可穿戴设备（如智能眼镜）产生大量第一人称视频，情景记忆问答（"我昨天见过的那个人叫什么？"）是核心用例。云端处理有隐私风险，但纯端侧方案又受限于计算资源。本文证明了一个中间路线的可行性：轻量级视频→文本记忆压缩 + 小规模 MLLM，在 8GB GPU 上即可运行，性能接近云端。

## 与移动端/端侧的相关性

高度相关。本文是可穿戴/边缘端侧记忆系统的直接研究，提供了完整的性能-隐私权衡数据和异步双线程架构设计参考，对构建真正实用的端侧记忆助手具有直接的工程指导价值。

## 参考文献

（参考文献待从原文补充）
