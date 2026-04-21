---
type: concept
tags: [hardware, cim, accelerator, edge, slm, co-design, 其他]
related: [[on-device-inference-memory-pressure]], [[mobile-aios-overview]], [[edge-cloud-offloading]]
sources:
  - url: https://arxiv.org/abs/2604.11512v1
    title: "EdgeCIM: A Hardware-Software Co-Design for CIM-Based Acceleration of Small Language Models"
    date: 2026-04
created: 2026-04-14
---

## 核心问题

The growing demand for deploying Small Language Models (SLMs) on edge devices, including laptops, smartphones, and embedded platforms, has exposed fundamental inefficiencies in existing accelerators. While GPUs handle prefill workloads efficiently, the autoregressive decoding phase is dominated by GEMV operations that are inherently memory-bound, resulting in poor utilization and prohibitive energy costs at the edge. In this work, we present EdgeCIM, a hardware-software co-design framework that rethinks accelerator design for end-to-end decoder-only inference. At its core is a CIM macro, imple

## 论文信息

- **标题**: EdgeCIM: A Hardware-Software Co-Design for CIM-Based Acceleration of Small Language Models
- **作者**: Jinane Bazzi, Mariam Rakka, Fadi Kurdahi
- **来源**: arXiv

## 方法/架构

详细方法论待补充。参考原始论文获取完整技术细节。

## 为什么重要

作为手机端 AIOS 生态的一部分，EdgeCIM：基于 CIM 的小语言模型硬件-软件协同设计 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[kv-cache-quantization-ondevice]] — 内存优化
