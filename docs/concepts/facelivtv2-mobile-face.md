---
type: concept
tags: [mobile, face-recognition, hybrid-architecture, cnn-transformer, edge]
related: [[fastshade-mobile-denoising]], [[edge-inference]], [[coremltools-9]]
sources:
  - http://arxiv.org/abs/2604.09127v1
created: 2026-04-14
---

# FaceLiVTv2：移动端高效人脸识别

面向边缘和移动设备的轻量级混合 CNN-Transformer 人脸识别架构。

## 架构改进
- **FaceLiVT** 的改进版本
- **全局-局部特征交互**：CNN 提取局部特征，Transformer 建模全局上下文
- **性能-效率平衡**：在识别精度和计算效率之间寻求更优的平衡点

## 约束条件
- 延迟限制
- 内存限制
- 能耗限制

## 为什么重要
人脸识别是手机解锁、支付认证的核心技术。FaceLiVTv2 的意义：
1. **混合架构趋势**：CNN + Transformer 的融合在端侧模型中越来越普遍
2. **端侧安全需求**：人脸识别必须在设备上本地运行（隐私要求）
3. **效率创新**：在严格约束下提升精度，直接影响用户体验
4. **与 [[coremltools-9]] 配合**：可转换为 Core ML 格式部署到 iOS

这类端侧 CV 模型是 [[mobile-aios]] 安全认证和摄像头功能的基础。
