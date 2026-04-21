---
type: concept
tags: [face-detection, forgery-detection, lightweight, mobile, edge, security, deepfake, cross-domain]
related: [[facelivtv2]], [[apple-intelligence]], [[coremltools-9]], [[ggml-llamacpp-hf]]
sources:
  - url: https://arxiv.org/abs/2604.10862
    title: "LRD-Net: A Lightweight Real-Centered Detection Network for Cross-Domain Face Forgery Detection"
    date: 2026-04-13
    reliability: high
created: 2026-04-22
updated: 2026-04-22
---

# LRD-Net：轻量级跨域人脸伪造检测

> 基于频域引导的轻量级人脸伪造检测网络，仅 2.63M 参数即可实现跨域泛化，适合移动端实时部署

## 核心问题

扩散模型驱动的深度伪造技术日益逼真，但现有检测方法面临两大瓶颈：
1. **跨域泛化差**：在未见过的伪造类型上性能急剧下降
2. **计算开销大**：无法部署在资源受限的移动端设备

传统的双分支架构（空间+频域并行处理）存在冗余计算，不适合实时场景。

## 方法/架构

LRD-Net 采用**序列式频域引导架构**，核心创新：

### 1. 多尺度小波引导模块（MWGM）
- 不并行处理空间和频域，而是用频域信号**指导**空间主干
- 基于离散小波变换生成多尺度注意力信号
- 注意力信号条件化 MobileNetV3 空间主干的特征提取

### 2. 真实中心学习策略
- 不直接建模多样化伪造模式（传统方法）
- 而是将特征表示锚定在真实人脸图像周围
- 使用指数移动平均原型更新 + 漂移正则化
- 通过真实分布的偏离程度检测伪造

### 3. 轻量化设计
- 主干网络：MobileNetV3（高效移动端骨干）
- 参数量：2.63M（比传统方法少约 9 倍）
- 支持 INT8 量化部署

## 实验结果

在 DiFF 基准上的跨域评估（来源：论文摘要）：

| 指标 | LRD-Net | 基线方法 |
|------|---------|---------|
| 跨域检测准确率 | SOTA | — |
| 参数量 | 2.63M | ~24M |
| 训练速度 | 8x+ 更快 | 基线 |
| 推理速度 | ~10x 更快 | 基线 |

**关键发现**：LRD-Net 在保持跨域泛化能力的同时，将计算量压缩到可实时部署的水平。这打破了"检测精度"与"计算效率"之间的传统权衡。

## 关键洞察

- **频域引导优于并行处理**：序列式架构用频域信号指导空间特征提取，避免了双分支的冗余计算，同时保留了频域信息的判别力
- **真实中心学习更高效**：建模"什么是真实的"比建模"什么是假的"更具泛化性，因为伪造模式是无限的但真实分布是有限的
- **轻量化的关键在于设计而非压缩**：从架构层面（MWGM + MobileNetV3）实现轻量化，而非后处理压缩

## 为什么重要

对手机端 AI 生态的意义：
- **移动端反欺诈**：可集成到手机人脸认证系统中，实时检测 deepfake 攻击
- **隐私保护**：本地化检测避免上传人脸数据到云端
- **边缘设备部署**：2.63M 参数适合 NPU/GPU 低功耗推理
- **与 FaceLiVTv2 互补**：FaceLiVTv2 聚焦活体检测，LRD-Net 聚焦伪造检测，两者可组合为完整的人脸安全方案

## 关联

- [[facelivtv2]] — 同为轻量级移动端人脸模型，活体检测方向
- [[apple-intelligence]] — Apple 端侧安全策略
- [[coremltools-9]] — 可通过 Core ML 部署到 iOS 设备
- [[ggml-llamacpp-hf]] — 可通过 GGUF 量化部署到跨平台边缘设备
