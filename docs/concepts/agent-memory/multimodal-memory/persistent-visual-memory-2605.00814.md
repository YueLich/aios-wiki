---
title: "Persistent Visual Memory: Sustaining Perception for Deep Generation in LVLMs"
arXiv: 2605.00814
date: 2026-05-01
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv API
---

# Persistent Visual Memory: Sustaining Perception for Deep Generation in LVLMs

**作者:** Siyuan Huang, Xiaoye Qu, Yafu Li, Tong Zhu, Zefeng He, Muxin Fu, Daizong Liu, Wei-Long Zheng, Yu Cheng
**发表:** 2026-05-01

## 摘要

While autoregressive Large Vision-Language Models (LVLMs) demonstrate remarkable proficiency in multimodal tasks, they face a "Visual Signal Dilution" phenomenon, where the accumulation of textual history expands the attention partition function, causing visual attention to decay inversely with generated sequence length. To counteract this, we propose Persistent Visual Memory (PVM), a lightweight learnable module designed to ensure sustained, on-demand visual perception. Integrated as a parallel branch alongside the Feed-Forward Network (FFN) in LVLMs, PVM establishes a distance-agnostic retrieval pathway that directly provides visual embeddings for precise visual perception, thereby structurally mitigating the signal suppression inherent to deep generation.

## 核心贡献

1. **Visual Signal Dilution 问题识别**: 首次系统定义和分析了 LVLM 在生成长文本时视觉注意力衰减的现象
2. **PVM 模块**: 轻量可学习的并行分支，在 FFN 旁路建立距离无关的视觉检索通路
3. **结构级缓解**: 直接注入视觉嵌入，结构性缓解深度生成中的信号抑制，而非依赖注意力的后处理
4. **对 Qwen3-VL 的广泛验证**: 在 4B 和 8B 规模均取得一致提升，尤其在需要持续视觉感知的复杂推理任务

## 实验结果

- PVM 为 Qwen3-VL 模型带来显著改进，参数 overhead 可忽略
- 在 4B 和 8B 规模均实现一致平均准确率提升
- 在需要持久视觉感知的复杂推理任务中提升最大
- PVM 能够抵抗序列长度诱导的信号衰减，加速内部预测收敛

## 为什么重要

揭示了 LVLM 长期对话中视觉感知衰退的根本原因（注意力的 partition function 被文本历史稀释），并提出了一个优雅的结构性解决方案。这对于需要生成长文本的多模态 Agent 系统（如视频描述、图文对话）具有重要价值。

## 与端侧/移动端的相关性

PVM 作为轻量并行分支插入 LVLM，参数 overhead 小，适合端侧部署。对于移动端的多模态 Agent（如拍照问答、视觉备忘录），PVM 可以确保在生成长响应时视觉感知不退化。
