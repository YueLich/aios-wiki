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

EdgeCIM 通过硬件-软件协同设计，针对 SLM 解码阶段的 GEMV 操作优化存算一体架构。详见下方详细方法。

## 为什么重要

作为手机端 AIOS 生态的一部分，EdgeCIM：基于 CIM 的小语言模型硬件-软件协同设计 对推动端侧 AI 落地具有重要意义。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[kv-cache-quantization-ondevice]] — 内存优化


## 详细方法

EdgeCIM 提出了端到端的硬件-软件协同设计：

- **硬件层面**：设计了专门针对 SLM 解码阶段 GEMV 操作的 CIM（存算一体）架构
- **软件层面**：开发了与 CIM 硬件特性对齐的模型映射和调度策略
- **协同优化**：硬件和软件联合设计，最大化存算一体架构的效率

SLM 推理分为 Prefill（GEMM 密集型）和 Decode（GEMV 密集型）两个阶段。对 LLaMA 的性能分析表明，解码阶段占总推理时间的 **70% 以上**，本质上是内存带宽受限的。CIM 通过在内存阵列内直接计算消除数据搬运瓶颈。

## 实验结果

- 在解码阶段实现了显著的加速效果（相比传统 GPU/NPU 方案）
- 能效比大幅提升，适合电池供电的移动设备
- 支持主流 SLM 架构（如 LLaMA 系列）

## 关键洞察

**解码阶段是真正的瓶颈**：大多数端侧推理优化关注 Prefill 阶段，但对于交互式应用场景（翻译、语音助手、对话），Decode 阶段才是真正的性能瓶颈。CIM 架构正是针对这一瓶颈的精准解决方案。

**边缘设备 ≠ 小型数据中心**：边缘设备的内存带宽和功耗约束与数据中心完全不同，需要专门的硬件架构，而非简单地缩小现有加速器。

## 更新关联
- [[rl-asic-exploration]] — 同样关注边缘 ASIC 设计，RL 驱动的架构搜索可以与 CIM 协同
- [[strix-npu-reliability]] — NPU 可靠性视角，CIM 架构需要考虑类似的系统级可靠性
- [[npu-scaling-testtime]] — 移动端 NPU 上的测试时计算扩展
- [[cimple-cim-attention-acceleration]] — 同为 CIM 方案，但关注注意力加速
