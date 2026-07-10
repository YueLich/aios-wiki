---
type: entity
tags: [diffusion-transformer, on-device, NPU, image-generation, hardware-optimization, edge-ai, quantization]
related: [[coremltools-9]], [[arm-computelibrary-v53]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2603.28405
    title: "EdgeDiT: Hardware-Aware Diffusion Transformers for Efficient On-Device Image Generation"
    date: 2026-03-30
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# EdgeDiT: 面向移动端 NPU 的硬件感知扩散 Transformer

> 专为手机 NPU 设计的高效图像生成 DiT 架构，通过硬件感知剪枝和结构优化实现端侧部署

## 核心问题

Diffusion Transformers (DiT) 在高保真图像合成方面达到了新的 SOTA，但其巨大的计算复杂度和内存需求严重阻碍了在资源受限的边缘设备上的本地部署。现有方法（如 DDPM、DDIM）的迭代去采样过程需要大量 GPU 资源，而移动设备上的 NPU（如 Qualcomm Hexagon 和 Apple Neural Engine）在架构上与 GPU 存在显著差异，直接迁移效率极低。

## 方法/架构

EdgeDiT 提出了一个硬件感知优化框架，系统性地识别并剪枝 DiT 中的结构冗余：

- **结构化剪枝**：分析 DiT 各层在目标 NPU 上的实际执行效率，识别并移除低效的注意力头和 FFN 维度
- **NPU 指令级优化**：针对 Hexagon HMX 和 Apple ANE 的矩阵乘法单元进行算子融合和内存布局优化
- **量化感知训练**：结合 INT8/INT4 量化，在保持生成质量的同时大幅降低计算和内存需求
- **延迟驱动搜索**：以实际 NPU 延迟（而非理论 FLOPs）为优化目标，确保工程上的真实收益

## 实验结果

- 相比原始 DiT 架构，FLOPs 显著减少
- 端侧延迟降低 **1.65 倍**，同时保持原始 Transformer 的缩放特性和表达能力
- 在标准图像生成基准测试中，生成质量（FID/CLIP Score）与原始模型相当
- 支持 Qualcomm Hexagon 和 Apple Neural Engine 双平台部署

## 关键洞察

EdgeDiT 的核心贡献在于证明了：**不是所有 DiT 组件对端侧部署都同等重要**。通过硬件感知的结构分析，可以找到对特定 NPU 架构"性价比"最高的子结构。这种思路比单纯的模型压缩（量化/蒸馏）更根本——它从架构设计层面就考虑硬件约束。

## 为什么重要

随着 Stable Diffusion 等图像生成模型在消费级应用中的普及，用户对隐私保护和离线使用的需求日益增长。EdgeDiT 证明了 Diffusion Transformer 可以在手机 NPU 上高效运行，为：
- **隐私敏感的图像编辑**（照片处理不上传云端）
- **离线创意工具**（随时随地的 AI 绘图）
- **低延迟实时生成**（AR 滤镜、实时风格转换）

提供了技术基础。这对小米 HyperAI、华为 HarmonyOS 等移动 AI 平台的图像生成功能具有直接的参考价值。

## 关联
- [[coremltools-9]] — Apple 端侧模型优化工具链
- [[arm-computelibrary-v53]] — ARM 端侧计算库
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力管理
- [[gemma4-ondevice]] — 另一个端侧部署的模型案例
