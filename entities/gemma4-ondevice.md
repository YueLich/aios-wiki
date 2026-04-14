---
type: entity
tags: [gemma, google, multimodal, on-device, model, android]
related: [[on-device-inference]], [[mobile-aios-overview]], [[apple-intelligence]]
sources:
  - url: https://huggingface.co/blog/gemma-4
    title: "Welcome Gemma 4: Frontier multimodal intelligence on device"
    date: 2026-04
created: 2026-04-14
---

# Gemma 4：端侧前沿多模态智能

## 概述

Google 发布 Gemma 4，这是 Gemma 系列的最新版本，专注于端侧多模态能力。支持视觉和语言理解，可在 Android 设备上本地运行。

## 关键特性

- **多模态**：支持图像和文本输入
- **端侧优化**：针对移动设备的推理效率优化
- **开放权重**：可在 HuggingFace 下载

## 为什么重要

Gemma 4 代表了 Google 在端侧 AI 战略上的重要一步。与 [[apple-intelligence]] 的 Apple Foundation Models 竞争，Gemma 4 通过开放生态（HuggingFace、[[llama.cpp]] 支持）吸引更多开发者。这是 [[mobile-aios-overview]] 中模型层的关键组件。

## 在 AIOS 中的角色

Gemma 4 可能成为 Android 生态中 [[on-device-inference]] 的默认选择之一，特别是在 [[xiaomi-hyperai]] 和三星 Galaxy AI 中。


## 核心问题

Quantization has been widely used to compress and accelerate inference of large language models (LLMs). Existing methods focus on exploring the per-token dynamic calibration to ensure both inference acceleration and model accuracy under 4-bit quantization. However, in autoregressive generation inference of long sequences, the overhead of repeated dynamic quantization and dequantization steps becomes considerably expensive. In this work, we propose MergeQuant, an accurate and efficient per-channel static quantization framework. MergeQuant integrates the per-channel quantization steps with the corresponding scalings and linear mappings through a Quantization Step Migration (QSM) method, thereby eliminating the quantization overheads before and after matrix multiplication. Furthermore, in vie

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[gemma]] — Gemma 模型家族
- [[on-device-inference]] — 端侧推理技术
- [[multimodal-edge-pruning]] — 多模态优化方法
