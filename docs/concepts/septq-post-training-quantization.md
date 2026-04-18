---
type: concept
tags: [quantization, llm, post-training, on-device, model-compression, 优化技术]
related:
  - "[[septq-post-training-quantization]]"
  - "[[septq-post-training-quantization]]"
  - "[[ggml-llamacpp-hf]]"
  - "[[mnn-350]]"
sources:
  - url: https://arxiv.org/abs/2604.10091
    title: "SEPTQ: A Simple and Effective Post-Training Quantization Paradigm for Large Language Models"
    date: 2026-04-14
created: 2026-04-14
---

## 核心问题

Large language models (LLMs) have shown remarkable performance in various domains, but they are constrained by massive computational and storage costs. Quantization, an effective technique for compressing models to fit resource-limited devices while preserving generative quality, encompasses two primary methods: quantization aware training (QAT) and post-training quantization (PTQ). QAT involves additional retraining or fine-tuning, thus inevitably resulting in high training cost and making it unsuitable for LLMs. Consequently, PTQ has become the research hotspot in recent quantization methods

## 论文信息

- **标题**: SEPTQ: A Simple and Effective Post-Training Quantization Paradigm for Large Language Models
- **作者**: Han Liu, Haotian Gao, Xiaotong Zhang
- **来源**: arXiv

## 方法/架构

详细方法论待补充。参考原始论文获取完整技术细节。

## 为什么重要

作为手机端 AIOS 生态的一部分，SEPTQ: 简单高效的 LLM 后训练量化范式 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[kv-cache-quantization-ondevice]] — 内存优化
