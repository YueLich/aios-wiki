---
title: "ScrapMem: A Bio-inspired Framework for On-device Personalized Agent Memory via Optical Forgetting"
arXiv: 2605.03804
date: 2026-05-05
tags: [agent-memory, memory-compression, multimodal, on-device]
reviewer: auto
source: arXiv RSS/API
---

# ScrapMem: A Bio-inspired Framework for On-device Personalized Agent Memory via Optical Forgetting

## 论文基本信息

- **作者**: Jiale Chang, Yuxiang Ren
- **arXiv**: https://arxiv.org/abs/2605.03804

## 摘要

长期个性化记忆对 LLM Agent 在资源受限边缘设备上的部署提出了挑战——高存储成本和多模态复杂性使得在端侧维持长期记忆极为困难。ScrapMem 将多模态数据整合为"剪贴簿页面"（Scrapbook Page），引入Optical Forgetting（光学遗忘）机制，逐步降低旧记忆的分辨率，在降低存储成本的同时抑制低价值细节。为保持语义一致性，ScrapMem 构建了情景记忆图（EM-Graph），将关键事件组织为因果-时序结构。在多模态 ATM-Bench 上的实验表明：ScrapMem 实现了 51.0% 的 Joint@10 得分（最优），通过光学遗忘减少高达 93% 的内存使用，并通过结构化聚合将 Recall@10 提升至 70.3%。

## 核心贡献

1. **ScrapMem 框架**: 将多模态数据整合为"剪贴簿页面"，支持端侧个性化 Agent 记忆
2. **Optical Forgetting 机制**: 逐步降低旧记忆的图像分辨率，93% 内存减少
3. **EM-Graph**: 因果-时序情景记忆图，保持语义一致性
4. **ATM-Bench 最优**: Joint@10 51.0%，Recall@10 70.3%

## 研究背景与问题

在资源受限的边缘设备（手机、手表、AR 眼镜）上部署 LLM Agent 时，长期个性化记忆面临双重挑战：存储成本高（多模态数据量大）和多模态复杂性（需要统一处理视觉、语言、轨迹等异构数据）。传统方法将所有记忆以相同精度存储，导致：
- 存储成本随时间线性增长
- 低价值细节占用宝贵存储
- 旧记忆分辨率不降低，无法优先保留新信息

## 核心方法

1. **Scrapbook Page 表示**: 将多模态记忆（图像、文本、轨迹）整合为统一页面格式
2. **Optical Forgetting（光学遗忘）**: 模仿人类视觉系统的周边视野模糊效应，逐步降低旧记忆分辨率：
   - 新记忆保持高分辨率
   - 随时间推移，分辨率逐步降低
   - 低价值细节（背景、噪声）被主动抑制
3. **EM-Graph 构建**: 将关键事件组织为因果-时序图结构：
   - 节点：关键事件、对象、动作
   - 边：因果关系、时序关系
   - 支持语义一致的检索和推理
4. **结构化聚合**: 通过 EM-Graph 的聚合提升检索召回率

## 为什么重要

ScrapMem 是首个专门针对端侧设备设计的个性化记忆框架，其 Optical Forgetting 机制提供了有理论基础的记忆压缩方法。对比传统的统一精度存储或简单过期删除，ScrapMem 通过渐进式分辨率调整保留了最有价值的记忆细节，同时大幅降低存储成本。EM-Graph 的引入解决了多模态记忆的语义一致性问题。

## 与移动端/端侧相关性

**高度相关**。ScrapMem 明确面向端侧设备设计：
- 93% 内存减少：对资源受限设备至关重要
- 多模态统一处理：适合手机/AR 眼镜的场景理解
- 渐进式压缩：无需一次性处理所有记忆，适合持续运行的移动 Agent
