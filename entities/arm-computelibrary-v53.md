---
type: entity
tags: [inference, arm, compute-library, sve, edge-hardware, optimization]
related: [[mnn-350]], [[llamacpp]], [[coremltools-9]], [[cnn-optimization-edge-ai-early-exits]]
sources:
  - url: https://github.com/ARM-software/ComputeLibrary/releases/tag/v53.0.0
    title: "ARM ComputeLibrary v53.0.0 Release"
    date: 2026-04-15
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# ARM ComputeLibrary v53.0.0

> ARM 官方神经网络计算库更新至 v53.0.0，新增 SVE TopKV 内核和 FreeBSD 实验性支持

## 核心变更

### Breaking Changes
- 新增张量尺寸检查，防止超大张量传入函数。某些之前能运行的大规模配置可能不再支持。

### 新增特性
- **SVE TopKV 内核**：为 ARM SVE（Scalable Vector Extension）架构添加 TopKV 算子的优化内核
- **FreeBSD 实验性支持**：扩展平台覆盖至 BSD 系统
- **NETopKV 函数**：新增神经引擎版本的 TopKV
- **验证函数 lvalue 支持**：改善 API 易用性

### Bug 修复
- 修复 `CpuGemmConv2d::run()` 中共享 gemm_output_3d 被意外修改的问题
- 移除 TopKV 比较中的 epsilon
- 修复 GPU-only debug 构建错误
- 多处索引验证增强（MaxUnpooling、Crop 等）
- 修复 Android NDK 构建时 CCFLAGS 未传递给汇编器的问题

## 为什么重要

ARM ComputeLibrary 是几乎所有 ARM 设备（手机、IoT、嵌入式）上神经网络推理的底层计算库。MNN、TFLite、ONNX Runtime 等推理框架都依赖它进行 ARM 优化。v53.0.0 的 SVE 内核扩展意味着：
- 未来 ARM 处理器（支持 SVE2 的 Cortex-X 系列）上 TopKV 运算将获得硬件加速
- 索引验证增强提高了端侧推理的健壮性——在资源受限环境中，越界访问比崩溃更危险
- FreeBSD 支持为特殊部署场景（路由器、NAS 等）打开了大门

## 关联
- [[mnn-350]] — 阿里 MNN 底层依赖 ARM ComputeLibrary 进行算子加速
- [[llamacpp]] — llama.cpp 的 ARM 后端同样使用 ComputeLibrary 的 GEMM 内核
- [[coremltools-9]] — Apple 的 ANE（Apple Neural Engine）是独立于 ARM CL 的优化路径
- [[cnn-optimization-edge-ai-early-exits]] — CNN 优化在 ARM 设备上的性能表现直接受 ComputeLibrary 版本影响
