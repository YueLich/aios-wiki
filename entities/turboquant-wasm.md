---
type: entity
tags: [wasm, simd, quantization, kv-cache, browser-inference, webgpu, gemma, vector-compression, 推理优化]
related: [[gemma4-ondevice]], [[ggml-llamacpp-hf]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://github.com/teamchong/turboquant-wasm
    title: "TurboQuant WASM GitHub"
    date: 2026-04-20
    reliability: high
  - url: https://arxiv.org/abs/2504.19874
    title: "TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate (Google Research, ICLR 2026)"
    date: 2026-04-20
    reliability: high
  - url: https://teamchong.github.io/turboquant-wasm/draw.html
    title: "Live Demo: Gemma 4 E2B Prompt-to-Excalidraw"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# TurboQuant WASM

> 基于 Google Research ICLR 2026 论文的向量量化库，通过 WASM + relaxed SIMD 和 WGSL GPU 着色器实现浏览器端 KV 缓存压缩，让 Gemma 4 E2B 在浏览器中实时运行。

## 核心问题

在浏览器中运行 LLM（如 Gemma 4）面临 KV 缓存的存储和计算瓶颈。140 层 × 35 个注意力头 × 30 tok/s 的 KV 缓存需要大量内存和带宽。原始 KV 缓存太大，无法在浏览器的有限内存中维持长对话。

## 方法/架构

TurboQuant 实现了一种在线向量量化算法，核心创新是 **极坐标 + QJL 旋转** 的组合压缩：

**双计算架构**：
- **WASM + relaxed SIMD**：用于 CPU 端的向量搜索、图像相似度、3D Gaussian Splatting 压缩等任务。Zig 编译为 WASM，利用 relaxed SIMD 指令集加速。
- **WGSL Compute Shaders**：用于 GPU 端的 LLM KV 缓存压缩。KV 缓存的 encode/decode/dot 操作需要 GPU 原生路径才能实时。Demo 中的着色器是参考实现。

**压缩原理**：
- 极坐标表示将高维向量映射到角度空间
- QJL (Quantized Johnson-Lindenstrauss) 旋转降低维度
- 在线自适应，无需预先训练码本
- 3 bits/dim 的压缩率，配合快速点积计算

**依赖要求**：relaxed SIMD 支持（Chrome 114+, Firefox 128+, Safari 18+, Node 20+）

## 关键数据

- npm 包 gzip 大小：~12kB
- GitHub Stars：267
- 压缩率：3 bits/dim
- 支持平台：所有现代浏览器 + Node.js
- 应用场景：向量搜索、图像相似度、3DGS 压缩、**LLM KV 缓存压缩**

## 关键洞察

1. **算法与实现分离**：同一 TurboQuant 算法在两个完全不同的计算平台上实现（WASM for CPU, WGSL for GPU），展示了跨平台推理优化的设计模式。

2. **浏览器成为 LLM 推理平台**：Gemma 4 E2B 在浏览器中运行 + TurboQuant 压缩 KV 缓存，意味着端侧 AI 不再局限于原生应用，Web 应用也能提供本地 AI 能力。

3. **Google Research 论文驱动的工程实现**：从 ICLR 2026 论文到可运行的浏览器 demo，学术研究到工程落地的周期在加速。

4. **KV 缓存压缩是端侧 LLM 的关键瓶颈**：模型大小可以通过量化解决，但 KV 缓存随序列长度线性增长，是长上下文推理的主要瓶颈。TurboQuant 提供了一种新的解决思路。

## 为什么重要

- **浏览器端 LLM 推理的基础设施**：TurboQuant 为 Web 端 AI 应用提供了核心的 KV 缓存压缩能力
- **跨平台推理优化范式**：WASM + WGSL 的双平台架构可推广到其他推理优化库
- **学术到工程的快速转化**：展示了如何将 ICLR 论文快速转化为可用的开源工具

## 关联

- [[gemma4-ondevice]] — Gemma 4 模型，TurboQuant 压缩其 KV 缓存
- [[kv-cache-quantization-ondevice]] — KV 缓存量化技术，TurboQuant 提供了新的实现方式
- [[ggml-llamacpp-hf]] — 同为端侧推理框架，但在 native 环境而非浏览器
- [[mlc-llm]] — 另一个浏览器/Web 端推理框架，可对比方案选择
