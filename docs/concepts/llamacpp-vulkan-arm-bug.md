---
type: concept
tags: [llama-cpp, vulkan, arm, 32-bit, gpu, bug, wearable, galaxy-watch, 推理优化, 边缘硬件]
related: [[ggml-llamacpp-hf]], [[edgecim-hardware-codesign]]
sources:
  - url: https://github.com/Perinban/llama.cpp/tree/axon-dev
    title: "llama.cpp axon-dev branch (fix)"
    date: 2026-04-20
    reliability: high
  - url: https://news.ycombinator.com/item?id=47774971
    title: "HN discussion"
    date: 2026-04-20
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# llama.cpp Vulkan 32-bit ARM GPU Bug

> 一个存在多年的隐性 bug 导致 llama.cpp 在所有 32-bit ARM 设备上 Vulkan GPU 后端静默失效，但 64-bit 设备不受影响。

## 核心问题

在 Samsung Galaxy Watch 4 Classic（armeabi-v7a, Mali G68）上运行 llama.cpp 时，Vulkan 后端报告 "33/33 layers offloaded to GPU"，但每个量化 MUL_MAT 操作都被拒绝。表面上 GPU 卸载成功，实际计算全部回退到 CPU。

## 根因分析

Bug 位于 `llama-model-loader.cpp` 的 `create_tensor()` 函数中：

1. **张量步长计算缺少块大小除法**：在计算 tensor stride 时，遗漏了对量化块大小的除法操作
2. **溢出级联**：错误的 stride 值传入 `ggml_nbytes()` 计算，导致缓冲区大小溢出
3. **32-bit vs 64-bit 差异**：在 64-bit 设备上，`size_t` 是 64 位，溢出值仍在 GPU 内存限制范围内，所以 GPU 计算虽然用错误的值但仍然"工作"。在 32-bit 设备上，`size_t` 是 32 位，溢出值超过 `max_buffer_size`，Vulkan 拒绝创建缓冲区。

**关键洞察**：这个 bug 在 64-bit 设备上完全不可见——它产生错误的值但不触发错误。只有在 32-bit ARM 设备上才会暴露。

## 影响范围

- **所有 32-bit ARM 设备**：包括 Android 手机（armeabi-v7a）、智能手表（Galaxy Watch 系列）、IoT 设备
- **仅 Vulkan 后端受影响**：CPU 后端和其他 GPU 后端（如 OpenCL）不受影响
- **存在时间**：bug 可能存在数年，直到有人在 32-bit 真实设备上测试才发现

## 关键洞察

1. **64-bit 隐蔽性**：这是一个典型的 "works on dev machines, fails on target devices" bug。开发环境几乎都是 64-bit，bug 被平台差异完全掩盖。

2. **可穿戴设备的推理挑战**：Samsung Galaxy Watch 等可穿戴设备的 32-bit 架构限制了 LLM 推理能力。即使修复了这个 bug，32-bit ARM 设备的内存限制（通常 <1GB 可用）仍然是根本瓶颈。

3. **端侧 AI 测试覆盖不足**：LLM 推理框架的测试主要在 x86_64 和 ARM64 上进行，32-bit ARM 的测试覆盖几乎为零。随着 AI 向可穿戴设备扩展，这需要改变。

## 为什么重要

- **可穿戴 AI 的现实检验**：在智能手表上运行 LLM 听起来很酷，但 32-bit 架构的限制（内存、精度）意味着需要专门的优化
- **量化推理的正确性**：量化计算的 bug 可能产生静默错误输出，不只是性能问题
- **跨平台测试的重要性**：端侧 AI 框架必须在真实目标设备上测试，不能只在开发机上验证

## 关联

- [[ggml-llamacpp-hf]] — 该 bug 所在的推理框架
- [[edgecim-hardware-codesign]] — 边缘硬件协同设计，涉及 ARM 架构优化
- [[kv-cache-quantization-ondevice]] — KV 缓存量化，类似的量化计算问题
