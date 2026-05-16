---
title: "SpaMEM: Benchmarking Dynamic Spatial Reasoning via Perception-Memory Integration in Embodied Environments"
arXiv: 2604.22409
date: 2026-04-24
tags: [agent-memory, multimodal-memory, embodied-ai, spatial-reasoning, benchmark]
reviewer: auto
source: arXiv
---

## 论文基本信息

- **作者**: Chih-Ting Liao, Xi Xiao, Chunlei Meng, Zhangquan Chen, Yitong Qiao
- **发表**: 2026-04-24
- **类别**: cs.CV

## 摘要

多模态大语言模型（MLLMs）已在静态视觉-空间推理方面取得进展，但在具身场景中往往无法保持长期空间一致性——信念需要随环境变化从自我中心视角持续修正。本文提出 SpaMEM（Space Memory from Action Sequences），一个大规模诊断基准，通过动作条件化的场景变换（spawn、place、remove）在长交互时域中隔离空间信念演化的机制。SpaMEM 构建于物理 grounded 数据集，包含 10,601,392 张高保真图像（RGB、深度、实例分割、语义分割四种模态），来自 1,000 个程序生成房屋中的 25,000+ 交互序列。论文将具身空间推理形式化为三级层次（15 个诊断任务）：Level 1 测量单次观察的原子空间感知；Level 2 通过 oracle 文本状态历史探查时间推理以排除感知噪声；Level 3 要求从原始视觉流进行端到端信念维持。实验揭示了一个一致的堆叠瓶颈：坐标一致的定位是一个难以突破的天花板，且 Level 2 到 Level 3 的急剧下降暴露了明显的符号脚手架依赖——模型在基于文本的记账时成功，但难以维持鲁棒的视觉记忆。

## 核心贡献

1. **SpaMEM 基准**：首个隔离空间信念演化机制的大规模诊断基准
2. **三级诊断层次**：原子感知 → 时间推理 → 端到端信念维持，逐层诊断瓶颈
3. **发现关键瓶颈**：符号脚手架依赖（text-based bookkeeping 成功但视觉记忆失败）
4. **发现坐标一致的定位是天花板**：多模态模型在视觉定位任务上存在系统性困难

## 为什么重要

为具身智能体的空间记忆研究提供了标准化诊断工具，揭示了当前 MLLMs 在视觉记忆维持上的根本性缺陷，对未来研究方向有重要指导价值。

## 与移动端/端侧的相关性

基准测试对评估端侧部署的视觉语言模型空间推理能力有直接价值，其发现也有助于在资源受限环境中针对性地改进视觉记忆模块。

---
*（参考文献待从原文补充）*
