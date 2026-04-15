---
type: concept
tags: [量化, deepfake-detection, edge-deployment, mobile-inference, real-time, post-training-quantization]
related: [[septq-post-training-quantization]], [[kv-cache-quantization-ondevice]], [[multimodal-edge-pruning]], [[fastshade-mobile-denoising]], [[facelivtv2-mobile-face]]
sources:
  - url: https://arxiv.org/abs/2604.08847
    title: "DeFakeQ: Enabling Real-Time Deepfake Detection on Edge Devices via Adaptive Bidirectional Quantization"
    date: 2026-04-15
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# DeFakeQ: 端侧实时 Deepfake 检测的自适应双向量化

> 首个面向 Deepfake 检测的量化框架——模型压缩至原始 10%，保留 90%+ 检测精度，已在真实手机上部署验证。

## 核心问题

Deepfake 检测对移动支付、视频会议、社交媒体至关重要，但现有检测器计算量过大：
- Xception-based 检测器需要 28M 参数、1.2G FLOPs
- 在高端手机 SoC 上推理延迟达 350ms，远超实时阈值
- 现有轻量化方案（剪枝、紧凑架构设计）仍依赖全精度权重，内存开销大
- **直接量化会破坏 Deepfake 检测的核心**：微表情不一致、细微纹理异常等超细粒度特征对量化噪声极为敏感

## 方法架构

DeFakeQ 包含两个核心创新模块：

### 水平自适应块量化 (HAQ - Horizontal Adaptive Block Quantization)
- 在每个 block 内逐层计算权重和激活的重要性
- 信息密度高的层分配更高比特宽度
- 信息密度低的层压缩更激进
- 目标：最小化信息损失的同时最大化计算和存储效率

### 垂直高效特征微调 (VEFT - Vertical Efficient Feature Fine-Tuning)
- 随机选择少量特征通道，恢复到全精度格式
- 构建渐进式对比度量学习损失函数
- 在量化 block 内保留判别性特征
- 补充 HAQ 的层级优化，进一步增强精度

**双向优化**：HAQ 横向自适应分配比特宽度，VEFT 纵向选择性恢复关键通道。两者协同工作。

## 实验结果

### 实验设置
- **数据集**：5 个 Deepfake 基准数据集
- **检测器**：11 个主流 SOTA/骨干 Deepfake 检测器
- **部署**：真实移动设备上的端到端验证

### 关键数据

| 指标 | 结果 |
|------|------|
| 参数压缩比 | 压缩至全精度的 **10%** |
| 精度保留 | 保留原始 **90%+** 检测性能 |
| 移动端部署 | 已在真实手机上验证实时推理 |
| 对比基线 | 显著优于现有轻量化设计和传统量化方法 |

### 与现有方案对比
- 优于轻量化架构设计（如 EfficientNet-based 检测器）
- 优于通用 PTQ 方法（如 AdaRound、BitSplit）
- 优于任务特定量化方法（通用计算机视觉量化无法处理 Deepfake 的特殊性）

## 关键洞察

1. **Deepfake 检测量化的独特挑战**：与一般分类不同，Deepfake 检测依赖超细微的面部伪造痕迹。标准量化方法会平滑掉这些关键特征。DeFakeQ 的自适应比特宽度分配解决了这个问题。

2. **双向优化的必要性**：仅做水平（层间）自适应不够——需要垂直（通道内）选择性恢复来保留判别性特征。两个维度缺一不可。

3. **从 350ms 到实时**：在手机 SoC 上将推理延迟从 350ms 降到实时级别，这意味着可以在用户拍照/视频通话时**即时**检测 Deepfake。

4. **实用价值**：论文已在真实手机上部署验证，不是实验室概念。这对移动支付、在线会议等场景有直接应用价值。

## 为什么重要

随着生成式 AI 的普及，Deepfake 威胁已从专业领域扩散到日常生活。用户主要通过手机进行视频通话、移动支付、社交分享——这些场景需要**即时、本地**的 Deepfake 检测。DeFakeQ 首次证明了在资源受限的移动设备上实现实时 Deepfake 检测的可行性，为端侧安全生态填补了关键空白。

## 关联
- [[septq-post-training-quantization]] — 通用 LLM 量化技术，DeFakeQ 是 Deepfake 检测领域的专门化量化
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化降低 LLM 内存，DeFakeQ 降低检测器内存
- [[multimodal-edge-pruning]] — 模态感知剪枝 vs 自适应量化，两种端侧优化路径
- [[fastshade-mobile-denoising]] — 移动端图像处理（去噪），DeFakeQ 是移动端视觉安全（检测）
- [[facelivtv2-mobile-face]] — 移动端人脸识别，DeFakeQ 专注于人脸伪造检测，两者构成移动端人脸安全双保险
