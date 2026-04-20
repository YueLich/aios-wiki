---
type: concept
tags: [inference, kv-cache, fp16, numerical-precision, quantization, 推理优化]
related: [[kv-cache-quantization-ondevice]], [[triton-dispatch-ragged-attention]], [[groupdpo-memory-efficient-preference-optimization]]
sources:
  - url: https://arxiv.org/abs/2604.15409
    title: "The Illusion of Equivalence: Systematic FP16 Divergence in KV-Cached Autoregressive Inference"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# KV-Cache FP16 精度陷阱：缓存与非缓存路径的系统性分歧

> KV 缓存长期被假定为数值等价的优化，但 FP16 下缓存-ON 和缓存-OFF 路径产生 100% 的 token 分歧率。来自 Ranjith Chodavarapu 等人 (arXiv 2604.15409)。

## 核心问题

KV 缓存是自回归 Transformer 推理中无处不在的优化，长期以来被假设为与无缓存计算在数值上等价。但这一假设在标准 FP16 精度下失败了。

## 方法/架构

**分歧机制**：
- 缓存-ON 和缓存-OFF 执行路径采用不同的浮点累加顺序
- 由于 FP16 的非结合性（non-associativity），不同的累加顺序产生确定性的 token 序列分歧
- 这不是采样随机性导致的——贪婪解码（greedy decoding）下同样出现 100% 分歧率

**实验设置**：
- 三个开源模型：LLaMA-2-7B、Mistral-7B-v0.3、Gemma-2-2B
- GSM8K 数据集评估
- 覆盖所有采样策略（greedy、top-k、top-p 等）

## 实验结果

- **100% token 分歧率**：在所有模型、所有采样策略下观察到完全分歧
- 贪婪解码也出现分歧，排除了采样随机性作为原因
- **缓存-ON 在 9 个条件中的 8 个获得更高准确率**
- 分歧方向是系统性的（systematic），而非随机的

## 关键洞察

这一发现对端侧推理有深远影响：

1. **量化叠加效应**：端侧推理通常使用 INT8/INT4 量化，比 FP16 精度更低。如果 FP16 已经产生系统性分歧，更低精度的分歧可能更严重且更不可预测
2. **跨设备一致性**：不同移动设备可能使用不同的推理引擎/硬件加速器，KV-Cache 实现差异会导致同一模型在不同设备上产生不同输出
3. **缓存可能有益**：缓存-ON 获得更高准确率的发现表明，KV-Cache 的数值"噪音"可能在某些情况下起到了正则化效果

## 为什么重要

- **端侧推理可靠性**：移动设备上的 KV-Cache 实现必须考虑 FP16 精度陷阱
- **量化推理验证**：INT8/INT4 量化的端侧模型需要验证缓存路径的数值稳定性
- **跨平台一致性**：不同手机的推理引擎输出可能不同，影响用户体验一致性

## 关联
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，面临更严重的精度问题
- [[triton-dispatch-ragged-attention]] — 推理优化的另一个维度
- [[groupdpo-memory-efficient-preference-optimization]] — 训练侧低精度优化
- [[ggml-llamacpp-hf]] — llama.cpp 的 KV-Cache 实现需注意此问题
