---
type: concept
tags: [taxonomy, survey, llm, scaling, 效率, 端侧推理, agentic]
related: [[slms-vs-llms]], [[edgeflow-cold-start]], [[kv-cache-quantization-ondevice]], [[networking-energy-agentic]], [[exectune-guide-core-policy]]
sources:
  - url: https://arxiv.org/abs/2601.14053v2
    title: "LLMOrbit: A Circular Taxonomy of Large Language Models"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# LLMOrbit: LLM 圆形分类体系

> 全面的 LLM 分类框架，涵盖 2019-2025 年 50+ 模型，揭示三大危机和六种突破范式

## 核心问题

LLM 领域发展迅速但缺乏系统性分类。从 Transformer 到推理系统，需要一个统一的框架来理解整个生态——尤其是当暴力扩展（brute-force scaling）遇到瓶颈时，哪些效率路径才是可持续的。

## 方法/架构：八维轨道模型

LLMOrbit 提出一个圆形分类法（Circular Taxonomy），将 50+ 模型按 8 个相互关联的维度组织：

- **架构创新**：Transformer 变体、MoE、MLA（Multi-head Latent Attention）
- **训练方法**：RLHF、GRPO、纯 RL、ORPO
- **效率模式**：量化、蒸馏、剪枝
- **推理优化**：测试时计算（test-time compute）
- **规模化路径**：从 14B 到 1.8T 参数
- **部署场景**：云端、边缘、端侧
- **能力维度**：语言、视觉、代码、推理
- **生态系统**：开源 vs 闭源，15 个组织

## 三大危机

论文识别出暴力扩展路线面临的三个根本瓶颈：

1. **数据枯竭**：9-27T token 将在 2026-2028 年耗尽
2. **成本爆炸**：5 年内从 $3M 飙升至 $300M+
3. **能耗不可持续**：22 倍增长

## 六种突破范式

论文发现 6 种方法正在打破扩展墙：

| 范式 | 代表 | 效果 |
|------|------|------|
| 测试时计算 | o1, DeepSeek-R1 | 10x 推理计算达到 GPT-4 性能 |
| 量化 | 多种方法 | 4-8x 压缩 |
| 分布式边缘计算 | 边缘部署 | 10x 成本降低 |
| 模型融合 | 多种方法 | 能力组合 |
| 高效训练 | ORPO | 内存减少 50% |
| 小型专用模型 | Phi-4 14B | 匹敌更大模型 |

## 关键洞察

- **后训练收益显著**：RLHF、GRPO、纯 RL 贡献巨大，DeepSeek-R1 在 MATH 上达到 79.8%
- **MoE 路由效率惊人**：18x 效率提升
- **MLA 压缩革命**：Multi-head Latent Attention 实现 8x KV cache 压缩，使 GPT-4 级性能成本低于 $0.30/M token
- **小模型崛起**：Phi-4 14B 等小型模型匹敌更大模型，这对端侧部署意义重大

## 为什么重要

这篇综述对手机端 AIOS 的核心价值在于：

1. **量化路线图**：4-8x 压缩直接关联端侧模型部署的可行性
2. **分布式边缘计算**：10x 成本降低验证了边缘推理的经济性
3. **小模型趋势**：Phi-4 14B 级别的模型匹配大模型，意味着端侧运行高质量 LLM 已经可行
4. **MLA + MoE**：这些架构创新直接降低端侧推理的内存和计算需求
5. **能耗分析**：22x 能耗增长不可持续，推动端侧推理成为必要选择

## 关联

- [[slms-vs-llms]] — 小型语言模型的能力边界，与 LLMOrbit 的小模型范式直接呼应
- [[edgeflow-cold-start]] — 端侧 LLM 冷启动优化，应对 LLMOrbit 指出的推理成本问题
- [[kv-cache-quantization-ondevice]] — KV cache 量化，与 MLA 的 8x 压缩原理互补
- [[networking-energy-agentic]] — Agent 推理的能耗分析，呼应 22x 能耗危机
- [[exectune-guide-core-policy]] — Guide Model 测试时计算范式的具体实现
