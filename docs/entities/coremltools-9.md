---
type: entity
tags: [toolchain, apple, coreml, model-conversion, inference, 平台]
related: [[apple-intelligence]], [[gemma-4-google]], [[minicpm]]
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
[[coremltools]] 是将 PyTorch/TensorFlow 模型转换为 [[core-ml]] 格式的唯一官方工具。9.0 对 Python 3.13 的支持意味着：
1. **开发体验升级**：开发者可以在最新 Python 版本上使用 coremltools
2. **生态兼容性**：与最新的 ML 库（如 [[mlx]]）保持兼容
3. **工具链成熟度**：Apple 持续维护说明端侧 ML 是长期战略

对于 [[mobile-aios]] 开发者而言，coremltools 是将自训练模型部署到 iOS/macOS 设备的关键桥梁。
