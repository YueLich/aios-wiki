---
type: entity
tags: [model, on-device, openbmb, quantization, multimodal]
related: [[gemma4-ondevice]], [[ggml-llamacpp-hf]], [[on-device-inference-memory-pressure]]
sources:
  - https://github.com/OpenBMB/MiniCPM/releases/tag/2.4.2
created: 2026-04-14
---

## 核心问题

The recent surge of Multimodal Large Language Models (MLLMs) has fundamentally reshaped the landscape of AI research and industry, shedding light on a promising path toward the next AI milestone. However, significant challenges remain preventing MLLMs from being practical in real-world applications. The most notable challenge comes from the huge cost of running an MLLM with a massive number of parameters and extensive computation. As a result, most MLLMs need to be deployed on high-performing cloud servers, which greatly limits their application scopes such as mobile, offline, energy-sensitive

## 论文信息

- **标题**: MiniCPM-V: A GPT-4V Level MLLM on Your Phone
- **作者**: Yuan Yao, Tianyu Yu, Ao Zhang
- **来源**: arXiv

## 方法/架构

详细方法论待补充。参考原始论文获取完整技术细节。

## 为什么重要

作为手机端 AIOS 生态的一部分，MiniCPM 2.4.2 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统参考
- [[mnn-350]] — 推理引擎
