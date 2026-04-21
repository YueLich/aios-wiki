---
type: concept
tags: [speculative decoding, Apple Silicon, MLX, on-device inference, 推理优化, 端侧推理, 波兰语LLM]
related: [[specguard-speculative-decoding]], [[wisv-device-edge-speculative-decoding]], [[vllm-mlx-apple-silicon]], [[driftwood-zero-copy-apple-silicon]], [[orion-apple-neural-engine-llm]], [[gemma4-audio-mlx]]
sources:
  - url: https://arxiv.org/abs/2604.16368
    title: "Cross-Family Speculative Decoding for Polish Language Models on Apple Silicon"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# Cross-Family Speculative Decoding on Apple Silicon

> 首个系统评估跨家族投机解码在 Apple Silicon 上表现的研究——证明上下文感知 Token 翻译是跨 tokenizer 配对的必要条件，而非可选优化。

## 核心问题

端侧 LLM 推理面临两大隐私和成本压力：(1) 云端推理将私人数据（文件、邮件、消息）发送到第三方服务器，对记者、法律从业者和企业不可接受；(2) API 成本长期看涨，当前云厂商亏本运营旗舰模型。投机解码（Speculative Decoding）通过小模型草稿 + 大模型验证的方式加速推理，但现有实现要求 draft 和 target 使用相同 tokenizer——这在低资源语言（如波兰语）中几乎不可能满足，因为同家族的小模型极少。

## 方法架构

### Universal Assisted Generation (UAG)

在 MLX-LM 投机解码流水线中增加 Token 翻译层，使不同 tokenizer 的 draft-target 配对成为可能：

**三层翻译策略对比：**

| 策略 | 原理 | 问题 |
|------|------|------|
| 无翻译 | 仅限同 tokenizer | 波兰语无同家族 draft 模型 |
| 朴素翻译 | 字符串往返（decode→encode） | 边界对齐丢失，单字符功能词（如波兰语介词 "w"）在不同位置获得不同 token ID |
| **上下文感知翻译** | 在重编码前预置已接受 token 窗口 | 保留位置信息，解决边界错位 |

**核心发现：** BPE tokenizer 对同一表面形式在不同上下文位置分配不同 token ID。波兰语中单字符功能词极多（如 "w" = "in"），naive string round-trip 丢失位置信息导致虚假拒绝。

### 实验配置

- **Target 模型：** Bielik-11B-v3.0-Instruct (8-bit 量化)
- **Draft 模型：** Bielik-1.5B、Llama-3.2-1B、Qwen2.5-1.5B（三个不同家族）
- **平台：** Apple Silicon (MLX)
- **数据集：** Wikipedia、pl_alpaca、Synthetic questions
- **评估：** n≥50 prompts/condition

## 实验结果

### Token 接受率 (k=2)

| Draft | 翻译策略 | Wikipedia | pl_alpaca | Synthetic |
|-------|---------|-----------|-----------|-----------|
| Bielik-1.5B | 无翻译 | 28.5% | 12.5% | 11.8% |
| Bielik-1.5B | 朴素 | 19.1% | 11.9% | 16.7% |
| Bielik-1.5B | **上下文感知** | **31.1%** | **23.9%** | **22.2%** |
| Llama-3.2-1B | 无翻译 | 26.7% | 12.1% | 10.6% |
| Llama-3.2-1B | 朴素 | 8.9% | 4.2% | 3.1% |
| Llama-3.2-1B | **上下文感知** | **42.0%** | **36.0%** | **36.5%** |
| Qwen2.5-1.5B | 无翻译 | 30.3% | 13.4% | 12.2% |
| Qwen2.5-1.5B | 朴素 | 10.5% | 6.4% | 4.9% |
| Qwen2.5-1.5B | **上下文感知** | **44.6%** | **41.0%** | **42.7%** |

**关键发现：** 上下文感知翻译在全部 9 个配置中取得最高接受率。朴素翻译对 Llama/Qwen 产生灾难性退化（3-10%），远低于无翻译。

### 吞吐量 (k=2)

| Draft | 条件 | Wikipedia TPS | Speedup | pl_alpaca TPS | Speedup |
|-------|------|--------------|---------|--------------|---------|
| — | 基线 | 14.83 | 1.00× | 14.70 | 1.00× |
| Llama-3.2-1B | 上下文感知 | **15.67** | **1.06×** | 14.22 | 0.97× |
| Qwen2.5-1.5B | 上下文感知 | **15.68** | **1.06×** | 14.44 | 0.98× |

在 Wikipedia 上实现 6% 加速，pl_alpaca 接近持平。所有 Bielik-1.5B 条件均低于基线（0.70-0.87×）。

### k=4 的反直觉发现

增加 draft 长度到 k=4 虽然提高接受率 6-13pp，但**所有 speedup 都显著下降**（0.46-0.70×）。这是因为：

> 在 Apple Silicon 统一内存架构上，草稿 token 的边际成本不可忽略，增大 k 是反生产力的，无论内容类型或 draft 选择。

## 关键洞察

1. **上下文感知翻译是必要条件，不是优化：** 对于跨 tokenizer 配对，没有上下文感知翻译，投机解码反而拖慢推理
2. **Apple Silicon 的独特约束：** 统一内存带宽改变了投机解码的经济模型——高带宽反而使二次开销项 βk² 更难承受，与 NVIDIA GPU 形成对比
3. **Break-even 接受率：** k=2 需要 38-53%，k=4 需要 81-90%——后者在实践中从未达到
4. **规模差距很重要：** 11B→1B (r≈0.071) 不如 70B→1B 有利，文献中的 speedup 结论不能直接移植到端侧小模型

## 为什么重要

对手机端 AI 生态的意义：
- **隐私保护推理：** 用户可运行本地 11B 模型 + 1.5B draft，完全避免数据上传
- **MLX 生态成熟度：** 展示 MLX-LM 的 UAG 扩展能力，为更多跨家族配对铺路
- **低资源语言可用性：** 波兰语等低资源语言没有同家族 draft 模型，UAG 是唯一实用方案
- **Apple Silicon 优化指导：** k=2 最优的结论可直接指导端侧部署策略

## 关联

- [[specguard-speculative-decoding]] — 另一种投机解码安全框架
- [[wisv-device-edge-speculative-decoding]] — 设备-边缘分布式投机解码
- [[vllm-mlx-apple-silicon]] — Apple Silicon 上 vLLM vs MLX 全面对比
- [[driftwood-zero-copy-apple-silicon]] — Apple Silicon 零拷贝 GPU 推理
- [[orion-apple-neural-engine-llm]] — 直接编程 Apple Neural Engine 运行 LLM
- [[gemma4-audio-mlx]] — Gemma 4 在 MLX 上的端侧音频处理
- [[transformers-to-mlx]] — 自动化模型移植到 MLX 框架
