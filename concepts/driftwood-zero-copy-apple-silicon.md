---
title: "Driftwood: Apple Silicon 零拷贝 GPU 推理"
tags: [apple-silicon, inference, edge-ai, webassembly, gpu, zero-copy]
---

# Driftwood: Apple Silicon 零拷贝 GPU 推理

## 概述

Driftwood 是一个实验性项目，利用 Apple Silicon 的统一内存架构（UMA）实现 WebAssembly（Wasm）沙箱到 GPU 的零拷贝数据传输，用于有状态 AI 推理。该项目验证了在 Apple Silicon 上，Wasm 线性内存与 Metal GPU 缓冲区可以共享同一物理内存，无需任何数据拷贝。

## 核心原理

### Apple Silicon 统一内存的特殊性

传统 GPU 架构（NVIDIA、AMD）中，CPU 和 GPU 内存通过 PCIe 总线分离，Wasm 沙箱到 GPU 的数据传输需要：

```
Wasm 线性内存 → 拷贝到宿主内存 → 拷贝到 GPU 内存
```

Apple Silicon 的 UMA 消除了这个边界——CPU 和 GPU 共享同一物理 DRAM。**关键问题**：能否将指针穿过抽象层（Wasm runtime → Metal API），保持零拷贝？

### 零拷贝链路的三个环节

| 环节 | 技术 | 验证 |
|------|------|------|
| **Link 1** | `mmap` + `MAP_ANON \| MAP_PRIVATE` | ARM64 macOS 返回 16KB 对齐地址（ARM64 页面大小），Metal 要求此对齐 |
| **Link 2** | `MTLDevice.makeBuffer(bytesNoCopy:length:)` | Metal 接受指针不拷贝，验证 `MTLBuffer.contents()` 与原始指针相同 |
| **Link 3** | Wasmtime `MemoryCreator` trait | 自定义内存分配器，使 Wasm 模块使用我们提供的 mmap 区域作为线性内存 |

### 数据流

```
mmap 区域 → Wasmtime（作为线性内存） → Metal（作为 GPU 缓冲区）
     ↓                                           ↓
Wasm 模块写入数据         GPU 读取同一内存进行计算
     ↓                                           ↓
Wasm 模块读取结果 ←←←←←←←←←←←←←←←←←←←←←←←←←←←←
```

全程无数据拷贝，无显式数据传输。

## 验证实验

### 测试内容

- **128×128 矩阵乘法**：Wasm 模块填充矩阵 A 和 B，GPU 运行 GEMM shader，模块读取结果 C
- **16,384 个元素**：零错误验证

### 三个验证维度

1. **指针一致性**：是否真正零拷贝？
2. **内存开销**：是否有隐藏拷贝？
3. **正确性**：GPU 看到的内容是否与 Wasm 写入一致？

## 对端侧 AI 推理的意义

### 技术启示

- **WebAssembly + Metal 在 Apple Silicon 上的潜力**：Wasm 沙箱的安全隔离与 GPU 加速推理可以兼得
- **统一内存架构是端侧推理的关键优势**：Apple Silicon 在这一点上领先 NVIDIA/AMD 的离散 GPU 架构
- **零拷贝路径对有状态推理尤其重要**：KV-Cache 等增量计算受益最大

### 局限性

- **仅适用于 Apple Silicon**：依赖 UMA 架构，不适用于离散 GPU
- **实验性质**：项目仍处于早期阶段，仅验证了基本矩阵乘法
- **生产化挑战**：Wasmtime 的 `MemoryCreator` 接口不保证稳定性

## 与其他端侧推理方案的对比

| 方案 | 零拷贝 | 沙箱隔离 | Apple Silicon 优化 | 状态 |
|------|--------|----------|-------------------|------|
| **llama.cpp Metal** | ✅ | ❌ | ✅ | 成熟 |
| **CoreML** | ✅ | ❌ | ✅ | 成熟 |
| **Driftwood** | ✅ | ✅ | ✅ | 实验性 |
| **Wasm + 传统 GPU** | ❌ | ✅ | N/A | N/A |

## 来源

- 博文：[abacusnoir.com](https://abacusnoir.com/2026/04/18/zero-copy-gpu-inference-from-webassembly-on-apple-silicon/)
- HN 讨论：[Zero-Copy GPU Inference from WebAssembly on Apple Silicon](https://news.ycombinator.com/item?id=0)
- 发布日期：2026-04-18
