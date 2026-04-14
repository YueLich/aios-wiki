---
type: entity
tags: [llama.cpp, metal, inference, ios, macos, ggml, xielu, activation, 推理框架]
related:
  - "[[llamacpp-b8786]]"
  - "[[mnn-inference-engine]]"
  - "[[coremltools]]"
sources:
  - https://github.com/ggml-org/llama.cpp/releases/tag/b8791
created: 2026-04-14
---

# llama.cpp b8791

llama.cpp 在 2026-04-14 发布 b8791 版本，距离上次 b8786 有 5 个 commit。

## 本次更新要点

### Metal: XIELU 一元运算符
- 在 Metal 后端新增 **XIELU (eXponential Identity Linear Unit)** 激活函数
- XIELU 是一种新型激活函数，结合了指数特性和线性特性，在某些场景下比 SiLU/Swish 表现更好
- 这意味着 **iOS/macOS 端侧推理** 可以使用更高效的激活函数，减少内存和计算开销
- 与 [[coremltools]] 的 CoreML 转换路径互补 — llama.cpp 走的是直接 Metal kernel 路线

### ARM NEON nvfp4 点积修复
- 修复了 ARM NEON 后端在 non-dotprod 目标上的 nvfp4 (NVIDIA FP4) 点积计算
- 对 Qualcomm Snapdragon 和 MediaTek 等无 dotprod 指令集的 ARM SoC 至关重要
- 确保低精度推理在更多移动芯片上正确运行

### 其他
- WebGPU 矩阵乘法改用 f32 累加（精度提升）
- BoringSSL 更新到 0.20260413.0
- Windows MSVC CMake 警告修复

## 为什么重要

XIELU on Metal 是端侧 LLM 推理优化的又一突破。传统的激活函数（ReLU, GELU, SiLU）在 Metal shader 中已有优化实现，XIELU 作为更新的激活函数被纳入 Metal kernel 后，使用 XIELU 架构的模型在 iPhone/Mac 上的推理效率将显著提升。结合 nvfp4 的 ARM 修复，llama.cpp 在移动芯片上的低精度推理能力持续增强。

## 相关
- [[llamacpp-b8786]] — 上一个版本，含更多架构更新
- [[mnn-inference-engine]] — 阿里端侧推理引擎，竞争方案
- [[coremltools]] — Apple 官方模型转换工具链
