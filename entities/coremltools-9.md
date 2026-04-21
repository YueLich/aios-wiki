---
type: entity
tags: [toolchain, apple, coreml, model-conversion, inference, 平台]
related: [[apple-intelligence]], [[gemma4-ondevice]], [[minicpm-242]]
sources:
  - https://github.com/apple/coremltools/releases/tag/9.0
created: 2026-04-14
---

# coremltools 9.0

Apple 官方的 Core ML 模型转换工具链，9.0 版本发布。

## 更新内容
- 新增 **Python 3.13** 支持
- 修复 `upsample_bilinear` 相关 bug
- 相比 8.3.0 版本（包含 9.0b1 的功能）

## 为什么重要
[[coremltools-9]] 是将 PyTorch/TensorFlow 模型转换为 [[coremltools-9]] 格式的唯一官方工具。9.0 对 Python 3.13 的支持意味着：
1. **开发体验升级**：开发者可以在最新 Python 版本上使用 coremltools
2. **生态兼容性**：与最新的 ML 库（如 ）保持兼容
3. **工具链成熟度**：Apple 持续维护说明端侧 ML 是长期战略

对于  开发者而言，coremltools 是将自训练模型部署到 iOS/macOS 设备的关键桥梁。

## 核心问题

Optically thick non-thermal synchrotron sources notably produce linear polarization vectors being parallel to projected magnetic field lines on the observer's screen, although they are perpendicular in well-known optically thin cases. To elucidate the complex relationship between the vectors and fields and to investigate the energy and spatial distribution of non-thermal electrons through the images, we perform polarization radiative transfer calculations at submillimeter wavelengths. Here the calculations are based on semi-analytic force-free jet models with non-thermal electrons with a power-law energy distribution. In calculated images, we find a $90^\circ$-flip of linear polarization (LP) vectors at the base of counter-side (receding) jet near a black hole, which occurs because of larg

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[mnn-350]] — 推理引擎
- [[kv-cache-quantization-ondevice]] — 内存优化
