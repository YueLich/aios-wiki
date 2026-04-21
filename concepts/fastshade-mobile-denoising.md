---
type: concept
tags: [mobile, inference, denoising, image-processing, mobile-gpu, quantization, lightweight]
related: [[gemma4-ondevice]], [[mnn-350]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.10275
    title: "FastSHADE: Fast Self-augmented Hierarchical Asymmetric Denoising for Efficient inference on mobile devices"
    date: 2026-04-11
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# FastSHADE: 移动端实时图像去噪

> 轻量级 U-Net 架构在 Qualcomm Adreno 840 GPU 上实现 <50ms 实时去噪 — Fanis London 2026

## 核心问题

现代移动摄影依赖高像素密度小型传感器，噪声水平远高于全画幅相机。深度学习 ISP 去噪是核心组件，但移动设备的延迟和功耗约束使实时高质量去噪成为开放难题。**挑战：在移动端 GPU 上同时满足 <50ms 延迟和高保真度**。

## 方法架构

### 1. 整体架构
FastSHADE 是一个基于结构重参数化的 U-Net 风格模型：
- 输入：含噪声 RGB 图像 (FP16，像素值 [0,255])
- 输出：预测干净残差，输出 = 输入 + 残差
- 模型内部处理数据归一化，直接接受整数像素值

### 2. 核心创新组件

**Asymmetric Frequency Denoising Block (AFDB)**：
- 将重空间结构提取与轻量高频噪声抑制解耦
- 优化计算资源分配——结构特征用深层网络提取，噪声抑制用轻量操作
- 最大化移动端 GPU 效率

**Spatially Gated Upsampler (SGU)**：
- 高分辨率跳跃连接的门控融合机制
- 乘法门控作为空间注意力，只传播必要的结构细节
- 不增加通道维度，提升 PSNR 同时保持推理速度

**Noise Shifting Self-Augmentation**：
- 从数据集图像直接生成统计有效的替代噪声样本
- 利用自然图像的局部平滑性假设：对噪声残差施加小随机空间平移 (±2像素)
- 避免引入合成噪声导致的域偏移问题

### 3. 模型家族
- **FastSHADE-M**：基础变体，<50ms 延迟，保持结构完整性
- **FastSHADE-XL**：放大版，建立图像质量新 SOTA

## 实验结果

MAI2021 基准测试：
- **速度-保真度 Pareto 前沿扩展**：FastSHADE 显著推高了边缘去噪的效率边界
- **FastSHADE-M**：Qualcomm Adreno 840 GPU FP16 推理 <50ms，实用级质量
- **FastSHADE-XL**：MAI2021 整体图像质量新 SOTA
- 相比超轻量方法（如 TLG），FastSHADE 在质量上有质的飞跃，同时延迟保持竞争力

## 关键洞察

- **结构重参数化是移动端模型的最优策略**：训练时用复杂结构提升容量，推理时等效简化为轻量结构
- **频率域解耦的工程价值**：AFDB 的非对称设计——重结构/轻噪声——是移动端高效推理的关键模式
- **自增强避免域偏移**：R2R 思路 + 空间平移 = 不引入合成噪声分布的数据增强
- **Pareto 前缘优化优于单一指标**：实用模型需要在速度和质量间找到平衡点

## 为什么重要

对手机端 AIOS 生态的意义：
- **移动端 ISP 流水线的去噪基准**：为其他移动视觉任务提供了效率-质量权衡的参考
- **FP16 移动 GPU 推理的工程范例**：展示了如何为特定硬件（Qualcomm Adreno）优化模型
- **轻量模型设计模式**：AFDB 的解耦思路可推广到其他移动端推理场景（目标检测、语义分割）
- **实时推理的延迟预算**：50ms 是移动端实时视觉的实用阈值，FastSHADE 证明了复杂模型在此约束下的可行性

## 关联
- [[mnn-350]] — 移动端推理引擎，FastSHADE 类模型的部署目标
- [[edgeflow-cold-start]] — 边缘设备推理优化
- [[gemma4-ondevice]] — 端侧模型部署
