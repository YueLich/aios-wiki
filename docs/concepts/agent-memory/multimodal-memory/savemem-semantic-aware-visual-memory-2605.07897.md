---
title: "Semantic-Aware Adaptive Visual Memory for Streaming Video Understanding"
arXiv: "2605.07897"
date: "2026-05-08"
tags: [agent-memory, multimodal-memory, memory-retrieval, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Semantic-Aware Adaptive Visual Memory for Streaming Video Understanding

## 论文基本信息

| 字段 | 内容 |
|------|------|
| **arXiv ID** | 2605.07897 |
| **作者** | Hang Wu, Sherin Mary Mathews, Yujun Cai, Ming-Hsuan Yang, Yiwei Wang |
| **发表日期** | 2026-05-08 |
| **方向** | 多模态记忆、视觉记忆、视频理解 |
| **代码** | 未公开 |

## 一句话总结

SAVEMem 是一个无需训练的视觉记忆系统，通过伪问题库引导的语义感知记忆生成和查询自适应的记忆检索范围，在流式视频理解任务上实现了 SOTA 性能，同时将 GPU 显存降低 48%。

---

## 摘要

在线流式视频理解要求模型处理连续的视觉输入并实时响应用户查询，其中无界流和不可预测的查询时机使记忆管理成为核心挑战。现有方法通常通过视觉相似性启发式压缩视觉 token，或在压缩完成后追加 KV-cache 级别的检索。然而，压缩决策很少融入语义信号，且检索往往在压缩确定后才添加，导致两阶段难以协调。

SAVEMem 提出了一个无需训练的双阶段框架，将语义感知融入记忆生成，并让检索范围随查询自适应调整。

**第一阶段**：SAVEMem 在恒定记忆预算下构建三层流式记忆在线。固定的伪问题库提供轻量级语义先验，使长期记忆的保留由语义显著性而非视觉相似性 alone 决定。**第二阶段**：SAVEMem 对该记忆执行查询感知检索。锚点条件的时间门（anchor-conditioned recency gate）根据查询目标是近期还是远期内容，自适应地将检索范围从短期扩展到中期和长期记忆。在该范围内，查询 token 与记忆 token 的后期交互选择候选帧进行回答。

在 Qwen2.5-VL 上无需训练即可应用，SAVEMem 将 OVO-Bench 总分从 52.27 提升至 62.69，在 StreamingBench 和 ODV-Bench 上也获得一致提升，同时在 128 帧下将峰值 GPU 显存降低 48%。

---

## 核心贡献

### 1. 三层流式记忆架构
SAVEMem 在恒定记忆预算下维护三层记忆：
- **短期记忆（Short-term）**：最近视觉帧的原始 token
- **中期记忆（Mid-term）**：基于伪问题库语义评分保留的帧
- **长期记忆（Long-term）**：经过语义压缩的持久记忆

三层分离避免了视觉相似性压缩导致的语义稀释问题。

### 2. 伪问题库（Fixed Pseudo-Question Bank）
SAVEMem 维护一组固定的伪问题（如 "发生了什么"、"谁在做什么"、"在哪里"），作为语义显著性的先验分布。与纯视觉相似性相比，语义评分能更好地保留对视频理解重要的帧，即使这些帧在像素层面相似度不高。

### 3. 锚点条件时间门（Anchor-Conditioned Recency Gate）
时间门根据查询内容自适应调节检索范围：
- 查询近期内容 → 检索范围聚焦短期记忆
- 查询远期内容 → 检索范围扩展到中期和长期记忆
- 查询同时涉及近期和远期 → 检索范围覆盖全部三层

### 4. 无需训练的设计
SAVEMem 完全无需训练，可直接应用于任意 VLM（视觉语言模型），通过即插即用的方式增强现有模型的流式视频处理能力。

---

## 实验结果

| 基准 | 基线分数 | SAVEMem 分数 | 提升 |
|------|----------|--------------|------|
| OVO-Bench Overall | 52.27 | 62.69 | +10.42 |
| StreamingBench | - | SOTA | 一致提升 |
| ODV-Bench | - | SOTA | 一致提升 |
| GPU 显存（128 帧）| 基线 | -48% | 显著降低 |

SAVEMem 在提升理解精度的同时大幅降低了计算资源消耗，展示了语义感知记忆管理的有效性。

---

## 为什么重要

1. **语义与感知的协同**：首次将语义先验融入视觉记忆压缩，解决了传统方法中"压缩-检索"两阶段分离的问题
2. **资源高效**：48% 显存降低对端侧部署具有重要意义，适合智能眼镜、无人机等受限设备
3. **训练免费**：无需微调，可直接提升现有 VLM 的流式视频处理能力

---

## 与端侧/移动端的相关性

- **显存优化**：48% 显存降低直接受益于移动/边缘设备的有限 GPU 资源
- **流式处理**：实时处理无界视频流，适合移动端视频分析场景（监控、AR）
- **即插即用**：无需重新训练，适合在已有移动端模型上集成

---

## 参考文献

- SAVEMem: Semantic-Aware Adaptive Visual Memory for Streaming Video Understanding (2026)
