---
type: concept
tags: [mobile, face-recognition, hybrid-architecture, cnn-transformer, edge, 其他]
related: [[fastshade-mobile-denoising]], [[on-device-inference-memory-pressure]], [[coremltools-9]]
sources:
  - http://arxiv.org/abs/2604.09127v1
created: 2026-04-14
---

## 核心问题

This paper introduces FaceLiVT, a lightweight yet powerful face recognition model that integrates a hybrid Convolution Neural Network (CNN)-Transformer architecture with an innovative and lightweight Multi-Head Linear Attention (MHLA) mechanism. By combining MHLA alongside a reparameterized token mixer, FaceLiVT effectively reduces computational complexity while preserving competitive accuracy. Extensive evaluations on challenging benchmarks; including LFW, CFP-FP, AgeDB-30, IJB-B, and IJB-C; highlight its superior performance compared to state-of-the-art lightweight models. MHLA notably impro

## 论文信息

- **标题**: FaceLiVT: Face Recognition using Linear Vision Transformer with Structural Reparameterization For Mobile Device
- **作者**: Novendra Setyawan, Chi-Chia Sun, Mao-Hsiu Hsu
- **来源**: arXiv

## 方法/架构

详细方法论待补充。参考原始论文获取完整技术细节。

## 为什么重要

作为手机端 AIOS 生态的一部分，FaceLiVTv2：移动端高效人脸识别 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[kv-cache-quantization-ondevice]] — 内存优化
