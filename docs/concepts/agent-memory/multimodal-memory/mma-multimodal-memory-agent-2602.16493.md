---
title: "MMA: Multimodal Memory Agent"
arXiv: 2602.16493
date: 2026-02-18
tags: [agent-memory, multimodal-memory]
reviewer: auto
source: arXiv API
---

# MMA: Multimodal Memory Agent

**作者:** Yihao Lu, Wanru Cheng, Zeyu Zhang, Hao Tang
**发表:** 2026-02-18

## 摘要

Long-horizon multimodal agents depend on external memory; however, similarity-based retrieval often surfaces stale, low-credibility, or conflicting items, which can trigger overconfident errors. We propose Multimodal Memory Agent (MMA), which assigns each retrieved memory item a dynamic reliability score by combining source credibility, temporal decay, and conflict-aware network consensus, and uses this signal to reweight evidence and abstain when support is insufficient. We also introduce MMA-Bench, a programmatically generated benchmark for belief dynamics with controlled speaker reliability and structured text-vision contradictions. Using this framework, we uncover the "Visual Placebo Effect", revealing how RAG-based agents inherit latent visual biases from foundation models.

## 核心贡献

1. **动态可靠性评分**: 结合来源可信度、时间衰减和冲突感知网络共识，为每个记忆条目分配动态可靠性分数
2. **证据重加权与弃权机制**: 当支持不足时主动弃权，而非输出低置信度答案
3. **MMA-Bench 基准**: 程序化生成的控制性基准，覆盖信念动态、说话者可信度和结构化图文矛盾
4. **Visual Placebo Effect 发现**: 揭示 RAG-based Agent 如何从基础模型继承隐性视觉偏差

## 实验结果

- 在 FEVER 上，MMA 在保持基线准确率的同时，方差降低 35.2%，选择性效用量提升
- 在 LoCoMo 上，安全导向配置提升了可操作准确率并减少了错误答案
- 在 MMA-Bench 上，MMA 在 Vision 模式下达到 41.18% Type-B 准确率，而基线在相同协议下崩溃至 0.0%

## 为什么重要

现有 RAG 记忆系统在检索时不区分记忆条目的质量，导致"垃圾进、垃圾出"。MMA 通过引入可靠性评分和冲突检测，解决了多模态记忆检索中的置信度校准问题，对于构建可信的多模态 Agent 系统有重要意义。

## 与端侧/移动端的相关性

MMA 的可靠性评分机制是轻量级的，可作为记忆检索的后处理过滤器应用于端侧。视觉偏见的发现对部署在移动设备上的多模态 Agent 具有警示意义——不能简单依赖 RAG 记忆，需要额外的置信度校准。
