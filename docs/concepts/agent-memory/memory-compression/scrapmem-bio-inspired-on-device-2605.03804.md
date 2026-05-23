---
title: "ScrapMem: A Bio-inspired Framework for On-device Personalized Agent Memory via Optical Forgetting"
arXiv: 2605.03804
date: 2026-05-05
tags: [agent-memory, memory-compression, on-device, multimodal-memory, selective-forgetting]
reviewer: auto
source: arXiv API
---

## 论文信息

- **标题**: ScrapMem: A Bio-inspired Framework for On-device Personalized Agent Memory via Optical Forgetting
- **arXiv ID**: 2605.03804
- **作者**: Jiale Chang, Yuxiang Ren
- **发表日期**: 2026-05-05
- **类别**: cs.AI

## 摘要（翻译）

LLM 智能体的长期个性化记忆在资源受限的端侧设备上面临高存储成本和多模态复杂性的挑战。为此，本文提出 ScrapMem，一个将多模态数据整合为"剪贴簿页面（Scrapbook Page）"的框架。ScrapMem 引入**光学遗忘（Optical Forgetting）**——一种光学压缩机制，对较旧的记忆逐步降低分辨率，降低存储成本同时抑制低价值细节。为保持语义一致性，构建了**情景记忆图（EM-Graph）**，将关键事件组织为因果-时序结构。在多模态 ATM-Bench 上的大量实验表明，ScrapMem 实现了三项主要优势：(1) 强性能，Joint@10 达到 51.0% 的新 SOTA；(2) 高存储效率，将存储成本降低至原来的 1/32；(3) 低计算开销，推理开销减少 40%。

## 核心贡献

1. **光学遗忘机制**：受生物遗忘过程启发，对旧记忆逐步降低视觉分辨率，在压缩存储的同时保留语义核心
2. **剪贴簿页面表示**：将多模态记忆（文本、图像、视频片段）整合为结构化的剪贴簿页面单元
3. **情景记忆图（EM-Graph）**：因果-时序图结构组织关键事件，支持语义一致性检索
4. **端侧优化**：1/32 存储成本 + 40% 推理开销 reduction，专为移动/可穿戴设备设计
5. **ATM-Bench 多模态基准**：涵盖多模态记忆存储、检索、更新综合评测

## 为什么重要

端侧 LLM 智能体（手机、手表、AR 眼镜）需要在极有限的存储和算力下维护长期记忆。ScrapMem 从两个正交维度解决这一问题：光学遗忘从感知层面压缩低价值细节，EM-Graph 从知识层面维护结构化语义。51% Joint@10 的 SOTA 性能与 32 倍存储压缩的组合，证明了在端侧实现高质量多模态记忆的可行性。

## 与移动端/端侧的相关性

ScrapMem 是目前最贴近移动端/可穿戴设备需求的记忆系统工作之一。光学遗忘机制特别适合摄像头驱动的记忆设备（如 AR 眼镜、随身摄像头），随着时间推移自动丢弃低价值视觉细节。EM-Graph 的结构化表示也更适合端侧推理引擎。1/32 存储压缩比使多模态记忆在手机本地存储中成为可能。

## 参考文献

（参考文献待从原文补充）
