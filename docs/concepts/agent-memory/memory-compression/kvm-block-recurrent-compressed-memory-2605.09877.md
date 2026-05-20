---
title: "Key-Value Means: Transformers with Expandable Block-Recurrent Compressed Memory"
arXiv: 2605.09877
date: 2026-05-11
tags: [agent-memory, memory-compression, memory-retrieval]
reviewer: auto
source: arXiv RSS/API
---

# Key-Value Means: Transformers with Expandable Block-Recurrent Compressed Memory

## 论文基本信息

- **arXiv ID**: 2605.09877
- **作者**: Daniel Goldstein, Eugene Cheah
- **机构**: Featherless AI
- **发表日期**: 2026-05-11
- **类别**: cs.LG (Machine Learning)
- **代码**: https://github.com/featherless-ai/KVM-paper
- **模型**: https://huggingface.co/collections/featherless-ai/kvm-paper

## 摘要

本文提出 **Key-Value Means（KVM）**，一种新型的块级循环（block-recurrence）注意力机制，可以兼容固定大小或可增长的记忆状态。为强基线 Transformer 配备固定大小 KVM 注意力层，可得到一个强大的 O(N) 分块 RNN，同时仅增加极少量新参数。

研究者训练了配备可增长 KVM 缓存的 Transformer，发现其在长上下文测试中具有竞争力的性能，且预填充（prefill）时间为亚二次方、状态增长为亚线性。KVM 可用标准操作实现，无需自定义 CUDA 内核，支持分块级并行训练和预填充。它在单一统一包中提供了传统 Transformer（可扩展上下文记忆、分块级并行训练和预填充）和线性 RNN 的诸多优势。

KVM 可在每一层使用，节省 KV-cache 内存，并允许在 O(N) 和 O(N²) 之间的预填充时间复杂度连续选择。也可与传统注意力层混合使用，在需要时补充 LRNN 层，实现更长的上下文。

## 核心贡献

### 1. 块级循环注意力（Block-Recurrent Attention）
将注意力计算限制在固定大小的块内，通过循环机制在块之间传递隐藏状态：
- 固定大小 KVM：产生 O(N) 分块 RNN，仅增加少量参数
- 可增长 KVM：支持 KV-cache 动态增长，性能逼近全注意力

### 2. 亚线性状态增长
相比标准 Transformer 的线性 KV-cache 增长，KVM 的状态增长为亚线性，大幅降低长序列的内存占用。

### 3. 亚二次方预填充时间
预填充时间复杂度可在 O(N) 到 O(N²) 之间连续选择，允许在速度和性能之间权衡。

### 4. 分块级并行化
训练和预填充均可分块级并行，无需串行处理整个序列，支持 GPU 高效利用。

### 5. 标准操作实现
无需自定义 CUDA 内核，用 PyTorch 标准操作即可实现，降低部署门槛。

## 为什么重要

Transformer 的 KV-cache 随序列长度线性增长是长上下文应用的主要瓶颈。现有方法如线性 RNN（LRNN）虽能压缩状态，但损失了 Transformer 的可扩展上下文记忆能力。KVM 在两者之间提供了灵活的权衡：

| 特性 | 标准 Transformer | 线性 RNN | KVM |
|------|-----------------|---------|-----|
| 上下文记忆 | 可扩展 | 有限 | 可扩展/固定可选 |
| 预填充复杂度 | O(N²) | O(N) | O(N) ~ O(N²) 连续 |
| 状态增长 | O(N) | O(1) | O(1) ~ O(N) 可选 |
| 并行训练 | 全序列 | 分块 | 分块 |

这种灵活性使 KVM 可以根据硬件和任务需求动态调整，对移动端/端侧部署尤为重要——可以根据设备能力选择合适的权衡点。

## 与移动端/端侧的相关性

- **端侧长上下文**：KVM 的亚线性状态增长使在移动设备上处理长文档、多轮对话成为可能，无需完整加载到 GPU。
- **可配置效率**：O(N) ~ O(N²) 的连续权衡让开发者可以在手机、嵌入式设备上选择合适的性能-效率平衡点。
- **标准实现**：无需自定义内核，可以用标准 PyTorch 部署，降低了端侧门槛。

## 参考文献

本文参考文献待从原文补充。
