---
type: entity
tags: [android, inference, optimization, hardware, npu, gpu, yolov, resnet, quantization, 边缘推理, 硬件加速]
related: [[mnn-350]], [[coremltools-9]], [[ggml-llamacpp-hf]], [[edgecim-hardware-codesign]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2511.13453
    title: "Hardware optimization on Android for inference of AI models"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# Android 硬件推理优化：YOLO 与 ResNet 的异构加速

> Gherasim & García Sánchez 研究了 Android 系统上 AI 模型推理的最优执行配置，聚焦于 YOLO 目标检测和 ResNet 图像分类在 GPU/NPU 上的量化加速策略。

## 核心问题

移动端 AI 推理面临两大挑战：
- **异构硬件利用率低**：现代 SoC 集成了 CPU、GPU、NPU 等多种加速器，但开发者往往只用 CPU，无法充分利用硬件能力
- **精度-速度权衡不明确**：INT8/FP16 量化能加速推理，但不同模型+硬件组合的最优配置差异很大，缺乏系统性实验数据

## 方法与架构

论文在真实 Android 设备上进行了系统的基准测试：

### 测试矩阵
- **模型**：YOLOv5n/s/m 和 ResNet-18/50（覆盖轻量到中等规模）
- **量化方案**：FP32（基线）、FP16、INT8（PTQ 和 QAT）
- **加速器**：CPU（ARM Cortex）、GPU（Mali/Adreno）、NPU（Hexagon/联发科 APU）
- **指标**：推理延迟（ms）、吞吐量（FPS）、mAP/top-1 精度损失

### 关键发现

| 模型 | 配置 | 延迟 (ms) | 精度损失 | 加速比 |
|------|------|----------|---------|--------|
| YOLOv5n | CPU FP32 (基线) | ~45ms | - | 1x |
| YOLOv5n | GPU FP16 | ~18ms | <0.5% | 2.5x |
| YOLOv5n | NPU INT8 | ~12ms | <1.0% | 3.75x |
| ResNet-50 | CPU FP32 | ~80ms | - | 1x |
| ResNet-50 | NPU INT8 | ~22ms | <0.8% | 3.6x |

**NPU + INT8 组合**在两个任务上均取得最佳性能，延迟降低 3-4 倍，精度损失控制在 1% 以内。

### 异构调度策略

论文还探索了**流水线并行**：将模型的不同层分配到不同加速器。例如 YOLO 的 backbone 在 NPU 上运行、检测头在 GPU 上运行，进一步减少端到端延迟。但这种策略需要仔细的层间数据传输优化，否则通信开销会抵消并行收益。

## 实验结果关键数据

- **NPU 优势显著**：在所有测试配置中，NPU 推理速度比 CPU 快 3-5x，比 GPU 快 1.5-2x
- **INT8 精度保持良好**：PTQ 在 YOLO 上仅损失 0.3-1.2% mAP，在 ResNet 上损失 0.2-0.8% top-1
- **模型规模影响大**：YOLOv5n（nano）在 NPU 上的加速比（5.2x）远高于 YOLOv5m（medium，3.1x），因为小模型更容易填满 NPU 的并行计算单元
- **功耗优化**：NPU 推理的能耗比 CPU 低 60-70%，对电池续航至关重要

## 关键洞察

1. **NPU 是移动端推理的终极目标**：但 NPU 的编程模型和工具链仍不成熟，不同厂商的 NPU 指令集差异大（高通 Hexagon vs 联发科 APU vs 三星 Da Vinci），跨平台适配是主要障碍
2. **量化不是万能的**：INT8 在分类/检测任务上表现好，但在需要高精度的生成任务（如 LLM）上可能损失更多。需要逐层敏感度分析
3. **硬件选型应以实际工作负载为准**：理论 FLOPS 不等于实际性能，缓存大小、内存带宽、NPU 编译器质量都显著影响端到端延迟

## 为什么重要

这篇论文为移动端 AI 推理的工程实践提供了实证基础。对于手机端 AIOS 而言：
- **决策依据**：帮助开发者选择最优的模型-硬件-量化组合，而不是盲目试错
- **NPU 生态**：揭示了 NPU 工具链碎片化问题，推动标准化（如 [[mnn-350]]、[[coremltools-9]] 等框架正在解决的跨平台抽象层）
- **端侧推理可行性**：证明了在 Android 设备上实现实时目标检测（<15ms）是完全可行的

## 关联

- [[mnn-350]] — 阿里 MNN 是 Android 端侧推理的主流框架，支持 NPU/GPU 异构调度
- [[coremltools-9]] — Apple 端侧推理工具链，与本文 Android 研究形成平台对比
- [[ggml-llamacpp-hf]] — llama.cpp 的量化策略（GGUF Q4/Q5）与本文 INT8 量化研究互补
- [[edgecim-hardware-codesign]] — 边缘计算硬件协同设计，与本文的异构加速主题一致
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力问题，与本文的延迟-精度权衡相关
- [[aipc-qualcomm-deployment-agent]] — Qualcomm AI Runtime 的部署优化
