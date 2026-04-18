---
title: "K-Token Merging: 潜在空间的 Token 压缩"
type: concept
created: 2026-04-19
source: arxiv
arxiv_id: "2604.15153"
tags: [inference, optimization, token-compression, llm, on-device, efficiency]
---

# K-Token Merging: 潜在空间的 Token 压缩

## 基本信息

- **论文**: [Compressing Sequences in the Latent Embedding Space: K-Token Merging for Large Language Models](https://arxiv.org/abs/2604.15153)
- **分类**: cs.CL, cs.AI
- **关键词**: token merging, latent space, prompt compression, quadratic attention

## 核心思想

K-Token Merging 是一种在**潜在嵌入空间**中压缩 token 序列的框架，通过轻量级编码器将连续的 K 个 token 嵌入合并为单个嵌入，从而降低自注意力的二次方复杂度。

### 问题背景

LLM 处理长 prompt 时面临的核心挑战：

- **二次方复杂度**: 自注意力的计算量随输入长度二次方增长
- **内存瓶颈**: KV 缓存随序列线性增长，限制了端侧设备的上下文窗口
- **现有方法局限**: 现有 prompt 压缩主要在 token 空间操作，忽略了潜在空间的冗余

### 方法创新

1. **潜在空间操作**: 在嵌入层面而非 token 层面进行压缩
2. **块级合并**: 将连续 K 个 token 的嵌入合并为单个表示
3. **轻量级编码器**: 使用小型网络学习最优合并策略
4. **可调节压缩比**: K 值可根据设备能力动态调整

## 对端侧推理的意义

| 指标 | 传统方法 | K-Token Merging |
|------|---------|-----------------|
| 注意力复杂度 | O(n²) | O((n/K)²) |
| KV 缓存大小 | O(n) | O(n/K) |
| 压缩粒度 | Token 级 | 潜在嵌入级 |
| 信息损失 | Token 语义丢失 | 更平滑的语义保留 |

## 应用场景

- **端侧长文档处理**: 在有限内存设备上处理更长上下文
- **RAG 系统优化**: 压缩检索到的文档，减少推理成本
- **多轮对话**: 压缩历史对话记录，维持更长的对话记忆

## 与其他技术的关联

- 与 [无损提示词压缩](lossless-prompt-compression.md) 互补：后者通过字典编码压缩重复数据
- 与 [Token Compression for ViT](token-compression-vit-acceleration.md) 对比：视觉 token 压缩 vs 语言 token 压缩
- 与 [KV Cache 量化](kv-cache-quantization-ondevice.md) 分别优化不同维度

## 参考链接

- [arXiv: 2604.15153](https://arxiv.org/abs/2604.15153)
