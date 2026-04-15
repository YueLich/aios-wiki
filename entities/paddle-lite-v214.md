---
type: entity
tags: [inference, paddle-lite, paddlepaddle, mobile, edge, chinese-ecosystem]
related: [[mnn-350]], [[ggml-llamacpp-hf]], [[coremltools-9]], [[edge-cloud-offloading]]
sources:
  - url: https://github.com/PaddlePaddle/Paddle-Lite/releases/tag/v2.14-rc
    title: "PaddlePaddle/Paddle-Lite: v2.14-rc"
    date: 2024-07-19
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Paddle-Lite v2.14-rc

> 百度飞桨的端侧推理引擎，适配 PaddleX 套件 4 个场景 8 个 Paddle 3.0 beta 模型，支持端侧 Arm CPU 和 OpenCL GPU 推理。

## 核心更新

v2.14-rc 适配 PaddleX 套件，支持以下 Paddle 3.0 beta 模型在端侧推理：

### 图像分类
- PP-LCNet_x1_0
- MobileNetV3_small_x1_0

### 目标检测
- PicoDet-S
- PicoDet-L

### 语义分割
- PP-LiteSeg-Tiny

### OCR
- PP-OCRv4-mobile-rec
- PP-OCRv4-mobile-det

## 技术特性

- **Arm CPU 推理**：针对 ARM 架构优化的推理内核
- **OpenCL GPU 推理**：利用移动端 GPU 加速
- **Paddle 3.0 兼容**：支持百度飞桨 3.0 beta 生态

## 为什么重要

Paddle-Lite 是中国 AI 生态的重要端侧推理引擎，与 MNN（阿里）、MindSpore（华为）并列三大国产端侧推理框架。虽然其发布节奏较慢（v2.14-rc 是 2024-07，最新仍是此版本），但它在百度飞桨生态中不可替代——PP-OCRv4、PicoDet 等模型在国内移动端应用广泛。

对手机端 AIOS 来说，Paddle-Lite 代表了"中国版 CoreML/MNN"的角色。如果手机端 AIOS 需要兼容百度飞桨模型，Paddle-Lite 是必经之路。

## 关联

- [[mnn-350]] — 阿里 MNN，同为国产端侧推理框架
- [[ggml-llamacpp-hf]] — llama.cpp，GGUF 生态的端侧推理
- [[coremltools-9]] — Apple CoreML 工具链
- [[edge-cloud-offloading]] — 端云协同卸载中的推理框架选型
