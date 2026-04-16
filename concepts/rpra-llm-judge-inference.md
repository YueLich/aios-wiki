---
type: concept
tags: [推理优化, LLM-Judge, 自评估, 模型路由, 效率, 小模型, 端侧推理]
related: [[edgeflow-cold-start]], [[septq-post-training-quantization]], [[gemma4-ondevice]], [[pAirZero-federated-finetuning]]
sources:
  - url: https://arxiv.org/abs/2604.12634
    title: "RPRA: Predicting an LLM-Judge for Efficient but Performant Inference"
    date: 2026-04-14
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# RPRA：用 LLM-Judge 预测实现高效推理

> 让小模型预测自己在 LLM-Judge 评估中的得分，通过报告卡（report card）和事后训练（hindsight training）实现高效的推理路由。2026 年 4 月 Meta/IDSIA 联合发表。

## 核心问题

当前 LLM 服务面临一个效率困境：
- 大模型（如 Llama 3.3 70B、GPT-120B）质量好但推理成本极高
- 小模型（如 MobileLLM 0.9B、Llama 3.2 1B/3B）成本低但质量不稳定
- 用户查询的难度差异巨大——简单查询用大模型是浪费，困难查询用小模型是失败

**核心问题**：如何让系统自动判断"这条查询我的小模型能处理好"？

## 方法架构

### 方法一：报告卡（Report Card）

为每个模型生成一份详细的"成绩单"：
1. 在多个数据集上评估模型的历史表现
2. 用 LLM-Judge（如 GPT-4）对模型输出评分
3. 基于模态评分构建性能描述
4. 将报告卡提供给模型作为上下文

**优势**：无需额外训练，适用于任何模型（包括闭源模型如 ChatGPT）

### 方法二：事后训练（Hindsight Training）

用"后见之明"微调模型：
1. 先用大模型生成输出
2. 用 LLM-Judge 评估这些输出的质量
3. 将评分作为额外训练信号微调小模型
4. 模型学会预测"如果我这样回答，Judge 会给我多少分"

**优势**：无需运行时携带报告卡，推理成本更低

### 关键发现

- **大模型表现好**：reasoning 模型（特别是大型推理模型）能较好地预测 Judge 评分
- **小模型校准差**：小模型通常过度自信或不够自信——这正是报告卡/事后训练需要解决的
- **报告卡效果显著**：MobileLLM 0.9B 在携带报告卡后，上下文预测精度大幅提升
- **事后训练最高效**：训练后的小模型无需额外上下文即可自评估

## 实验结果

评估覆盖模型：MobileLLM 0.9B、Llama 3.1 8B、Llama 3.2 1B/3B、Llama 3.3 70B、GPT OSS 20B/120B、DeepSeek Distilled 14B/32B/70B、Llama 4 Scout

关键数据点：
- **AIME 2024**：最小模型（1B-3B）在事后训练后精度提升最为戏剧化
- **MedQA**：即使大型非推理模型，报告卡也带来显著改善
- MobileLLM 0.9B 在事后训练后，上下文预测精度接近更大的模型

## 关键洞察

1. **自知之明的价值**：让模型知道自己"能做好什么"比让模型"什么都能做"更具实际价值
2. **路由而非替代**：RPRA 不是替代大小模型，而是实现智能路由——简单查询用小模型、困难查询升级到大模型
3. **端侧可行性**：MobileLLM 0.9B 级别的模型在事后训练后能有效自评估，这对端侧部署意义重大
4. **报告卡的泛化性**：无需训练即可为任何模型（包括闭源）提供自评估能力

## 为什么重要

对于手机端 AIOS 生态：
- **智能模型路由**：端侧小模型可以自判断是否需要云端大模型辅助，实现端云协同推理
- **成本优化**：90%+ 的简单查询可以用小模型处理，仅在需要时升级到大模型
- **用户体验**：系统可以透明地在质量和速度之间权衡，用户感知不到路由过程
- **端侧自适应**：模型可以根据自身报告卡动态调整行为

## 关联
- [[edgeflow-cold-start]] — 端侧 LLM 冷启动优化，RPRA 可用于决定何时加载大模型
- [[septq-post-training-quantization]] — 量化小模型 + RPRA 自评估 = 高效端侧推理
- [[gemma4-ondevice]] — Gemma 4 作为端侧小模型可受益于 RPRA 路由
- [[pAirZero-federated-finetuning]] — 事后训练可在联邦微调框架中实现
