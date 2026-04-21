---
type: concept
tags: [WebGPU, KV Cache, 端侧推理, Gemma, 浏览器推理, 模型压缩, ICLR 2026]
related: [[gemma4-ondevice]], [[kv-cache-quantization-ondevice]], [[llamacpp]]
sources:
  - url: https://teamchong.github.io/turboquant-wasm/draw.html
    title: "Prompt to Diagram: Gemma 4 E2B in Browser via WebGPU"
    date: 2026-04-20
    reliability: medium
  - url: https://arxiv.org/abs/2504.19874
    title: "TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate"
    date: 2026-04-20
    reliability: high
  - url: https://github.com/teamchong/turboquant-wasm
    title: "TurboQuant WASM - GitHub"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# TurboQuant + Gemma 4 浏览器推理 — WebGPU 上的端侧 LLM

> 基于 Google Research 的 TurboQuant 算法（ICLR 2026），通过 WGSL compute shader 在浏览器中压缩 Gemma 4 E2B 的 KV Cache，实现 30+ tok/s 的端侧推理。Demo 展示了 Gemma 4 在浏览器中生成 Excalidraw 图表。

## 核心问题

端侧 LLM 推理的两大瓶颈：**内存带宽**和**上下文长度**。KV Cache 是推理时最大的内存占用——140 层 x 35 个注意力头 x 序列长度，每层的 Key 和 Value 都需要缓存。在浏览器/WebGPU 环境下，GPU 内存比服务器更受限，KV Cache 压缩直接决定能否运行。

## 方法/架构

### TurboQuant 算法

TurboQuant 是 Google Research 在 ICLR 2026 发表的向量量化算法：

- **Polar + QJL 旋转**：将向量分解为极坐标形式，再通过 QJL (Quantized Johnson-Lindenstrauss) 变换压缩
- **~2.4x KV Cache 压缩**：140 层的 KV Cache 从约 3GB 压缩到约 1.25GB
- **直接在压缩数据上计算**：不需要解压即可执行点积运算（attention score 计算）
- **无需训练步骤**：不像 PQ/OPQ 需要码本训练，只需 init() 即可编码任意向量
- **6x 向量压缩**：1M x 384-dim 的 embedding 索引从 1.5GB 压缩到 240MB

### 双子系统架构

TurboQuant 提供两套运行时：

**WASM + Relaxed SIMD（CPU 向量搜索）**：
- npm 包 ~12kB gzip
- Node.js 和浏览器均可使用
- 适合图像相似度搜索、3DGS 压缩

**WGSL Compute Shaders（GPU LLM 推理）**：
- 浏览器 Demo，Chrome 134+ only
- 30+ tok/s 推理速度
- 需要 WebGPU subgroups 支持

### Gemma 4 E2B 浏览器 Demo

- **模型**：Gemma 4 E2B (2B 激活参数 MoE)
- **运行环境**：桌面 Chrome 134+，WebGPU subgroups 支持
- **推理速度**：30+ tok/s（WGSL compute shader 实现）
- **内存需求**：~3GB RAM（mobile browsers 目前 cap 远低于此）
- **功能**：文字描述 -> Excalidraw 矢量图生成
- **输出优化**：LLM 输出紧凑代码 (~50 tokens) 而非原始 JSON (~5,000 tokens)

### WGSL Shader 实现

TurboQuant 的核心数学（polar 分解 + QJL 旋转 + 符号打包/解包）全部在 WGSL compute shader 中实现：
- dotBatch() 自动检测 WebGPU，在 GPU 上直接扫描压缩向量
- 不可用时透明回退到 WASM relaxed SIMD
- SIMD 向量化的 QJL 符号打包/解包和缩放

## 实验结果/关键数据

| 指标 | 值 |
|------|-----|
| KV Cache 压缩比 | ~2.4x |
| 推理速度 | 30+ tok/s |
| 模型大小（E2B） | ~3.1GB |
| 浏览器最低版本 | Chrome 134 |
| 内存需求 | ~3GB RAM |
| 输出 token 压缩 | ~100x (50 tokens -> 5000 tokens JSON) |

## 关键洞察

1. **浏览器是下一个端侧推理平台**：WebGPU 的普及使得在浏览器中运行 LLM 成为现实。不需要安装任何软件，打开网页即可使用。
2. **KV Cache 压缩比模型权重压缩更关键**：端侧推理的瓶颈不是模型加载（E2B 只有 3GB），而是推理时 KV Cache 的增长。TurboQuant 的 2.4x 压缩直接影响可支持的上下文长度。
3. **输出格式优化比模型优化更有效**：Demo 证明让 LLM 输出紧凑代码（50 tokens）而非原始 JSON（5000 tokens）能带来 100x 的效率提升——这比任何推理优化都更立竿见影。
4. **Mobile 端仍是瓶颈**：3GB RAM 需求远超当前 mobile browser 的 cap。需要 WebAssembly GC 或更激进的量化方案才能在手机浏览器中运行。

## 为什么重要

- 展示了端侧 LLM 推理的全新范式：**浏览器即推理引擎**
- TurboQuant 的 KV Cache 压缩算法对所有端侧推理方案（llama.cpp、MNN、MLC-LLM）都有参考价值
- 证明了 MoE 模型（E2B 激活 2B）在消费级 WebGPU 上的可行性
- Google Research 的算法 + 独立开发者实现，体现了开源 AI 社区的活力
- 为端侧 Agent 的 UI 交互提供了新思路：Agent 可以在浏览器中直接生成可视化内容

## 关联

- [[gemma4-ondevice]] — Gemma 4 模型家族概述，本页面是其浏览器部署方案
- [[kv-cache-quantization-ondevice]] — 端侧 KV Cache 量化技术对比，TurboQuant 是最新的方案
- [[llamacpp]] — llama.cpp 的 KV Cache 优化是另一条技术路线
