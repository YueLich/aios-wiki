---
type: entity
tags: [llama.cpp, qualcomm, hexagon, inference, optimization, on-device, mobile]
related: [[llamacpp-b8795]], [[llamacpp-b8793]], [[ggml-llamacpp-hf]], [[mnn-350]], [[edgecim-hardware-codesign]]
sources:
  - url: https://github.com/ggml-org/llama.cpp/releases/tag/b8797
    title: "llama.cpp b8797 Release"
    date: 2026-04-15
    reliability: high
created: 2026-04-15
updated: 2026-04-15
---

# llama.cpp b8797 — Qualcomm Hexagon HMX 矩阵乘法优化

> 本次发布聚焦 Qualcomm Hexagon DSP 的 HMX 矩阵乘法单元异步优化，是 llama.cpp 在骁龙设备上推理性能的重大提升。发布时间：2026-04-15。

## 核心问题

Qualcomm Hexagon DSP 拥有 HMX（Hexagon Matrix eXtension）硬件矩阵乘法单元，但在之前的 llama.cpp 实现中，HMX 调用是同步的——主线程发出 matmul 请求后必须等待 HMX 计算完成才能继续，导致 HVX（向量单元）的反量化和 DMA 数据传输阶段被阻塞。这种串行执行模式无法充分利用 Hexagon DSP 的异构计算能力。

## 方法/架构

b8797 引入了三项核心技术改进：

### 1. 异步 HMX Worker（hmx-worker → hmx-queue）
- **原始方案**：同步 HMX 调用，主线程阻塞等待 matmul 完成
- **新方案**：引入专用的 hmx-worker 线程，将 HMX 计算与 HVX 反量化/DMA 传输流水线化
- **架构演化**：从 hmx-worker 进一步简化为 hmx-queue，复用 dma-queue 接口，减少线程唤醒往返次数
- **效果**：HMX matmul 与 HVX dequant/DMA 三个阶段真正并行执行

### 2. Cost-based VTCM Chunk Search
- 针对 out-stationary matmul 模式，实现了基于代价的 VTCM（Vector Tightly Coupled Memory）分块搜索
- VTCM 是 Hexagon DSP 的片上高速缓存，合理分块可最大化数据局部性

### 3. 其他优化
- **Scatter/Transpose 优化**：使用 HMX 内联函数替代通用实现
- **VTCM 内存限制调整**：在 v73 架构上将 vmem 上限调至略低于 3GB
- **竞态修复**：修复 hmx_worker_drain 中的 futex 竞态条件，通过局部变量存储避免重复原子加载

## 实验结果/关键数据

| 优化项 | 影响 |
|--------|------|
| 异步 HMX worker | HVX 与 HMX 并行，吞吐量提升 |
| hmx-queue 接口 | 减少线程唤醒开销 |
| VTCM chunk search | 改善数据局部性 |
| vmem limit 调整 | 支持更大模型 |

本次发布同时包含 iOS XCFramework 构建，表明 llama.cpp 在 Apple 生态（CoreML 对比路径）和 Qualcomm 生态上同步推进。

## 关键洞察

**Hexagon DSP 正成为移动端 LLM 推理的关键战场。** Qualcomm 的 HMX 单元类似 Apple 的 AMX/ANE，是专门为矩阵运算设计的硬件加速器。llama.cpp 的这次优化意味着：

1. **骁龙设备的 LLM 推理差距在缩小**：之前 Hexagon DSP 的利用率不高，这次优化后有望显著提升 tokens/s
2. **Qualcomm 的开源投入在加深**：PR 由 Qualcomm 工程师（@qti.qualcomm.com）主导提交，表明 Qualcomm 在积极支持 llama.cpp 生态
3. **异步流水线是移动端推理的通用优化模式**：类似 Apple ANE+GPU 的异构调度思路

## 为什么重要

对手机端 AI 生态的意义：
- **直接利好骁龙 8 Gen 4/8s Gen 4 设备**：这些芯片的 Hexagon DSP 拥有更强的 HMX 能力
- **缩小与 Apple Silicon 的差距**：llama.cpp 在 iOS/macOS 上已有成熟的 CoreML 路径，现在 Qualcomm 路径也在快速追赶
- **为端侧 Agent 提供更低延迟的推理基础**：异步流水线减少了首 token 延迟

## 关联
- [[llamacpp-b8795]] — 前序版本，对比优化趋势
- [[llamacpp-b8793]] — 更早的版本，可观察迭代方向
- [[ggml-llamacpp-hf]] — GGML 与 HuggingFace 合并后的生态基础
- [[mnn-350]] — 阿里 MNN 同样在 Qualcomm 平台上竞争
- [[edgecim-hardware-codesign]] — 硬件软件协同设计的端侧推理趋势
- [[rl-asic-exploration]] — 从 LLM 到芯片的 RL 驱动架构探索
