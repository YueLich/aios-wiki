---
type: entity
tags: [端侧模型, Meta, LLM, 1B参数, on-device, quantization-aware, long-context]
related: [[mobilefinetuner]], [[gemma4-ondevice]], [[llama32]], [[minicpm-242]]
sources:
  - url: https://arxiv.org/abs/2511.06719
    title: "MobileLLM-Pro Technical Report"
    date: 2025-11-10
    reliability: high
  - url: https://huggingface.co/collections/facebook/mobilellm-pro
    title: "MobileLLM-Pro Weights & Code"
    date: 2025-11-10
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# MobileLLM-Pro

> Meta Reality Labs 推出的 10 亿参数端侧语言模型，11项基准全面领先 Gemma 3-1B 和 Llama 3.2-1B。

## 核心问题

在 sub-2B 参数级别实现强性能 + 长上下文 + 量化鲁棒性，是端侧 AI 的核心挑战。
Meta 需要一个能在手机、笔记本、穿戴设备上高效运行的紧凑模型。

## 方法/架构

四项核心创新：

1. **隐式位置蒸馏（Implicit Positional Distillation）**：通过知识蒸馏将长上下文能力注入小模型，支持 128K token 上下文窗口
2. **专家模型合并框架（Specialist Model Merging）**：将多个领域专家融合为紧凑模型，不增加参数量
3. **模拟驱动数据混合（Simulation-Driven Data Mixing）**：基于效用估计的数据配比优化
4. **4-bit 量化感知训练 + 自蒸馏（QAT + Self-Distillation）**：训练时即考虑量化，4-bit 量化后性能几乎无损

## 实验结果

- **11 项标准基准** SOTA，显著超越 Gemma 3-1B 和 Llama 3.2-1B
- 支持 **128K token 上下文**（长上下文场景：文档理解、长对话）
- **4-bit 量化** 后仅有轻微性能退化（适合 INT4 部署）
- 模型权重和代码已在 HuggingFace 开源

## 关键洞察

MobileLLM-Pro 代表了"小而精"路线的最新成果。
隐式位置蒸馏是关键突破——直接训练长上下文对1B模型太难，但蒸馏让它变得可行。
量化感知训练（QAT）确保了模型在真实部署场景（INT4）下的可用性。
专家合并避免了 MoE 的高内存开销，用合并达到类似效果。

## 为什么重要

- **Meta 的端侧战略**：继 MobileLLM 初版后的重要迭代，Meta 将端侧视为核心赛道
- **128K 上下文**：1B 模型支持 128K 是前所未有的，解锁长文档、长对话场景
- **量化友好**：4-bit 几乎无损 = 实际手机部署可行
- **开源**：权重+代码开源，加速社区端侧 AI 生态

## 关联
- [[mobilefinetuner]] — MobileFineTuner 可在手机上微调 MobileLLM-Pro
- [[gemma4-ondevice]] — Google 的端侧模型竞争者
- [[llama32]] — Meta 的另一端侧模型线
- [[minicpm-242]] — 面壁智能的端侧模型，同赛道竞争
- [[quantization-techniques]] — QAT 是量化的一种高级形式
