---
type: concept
tags: [移动端视觉, 超分辨率, 图像处理, 模型优化, 移动端部署, NTIRE]
related: [[adavfm-adaptive-vfm-edge]], [[secagent-mobile-gui]], [[a-io-adaptive-inference]]
sources:
  - url: https://arxiv.org/abs/2604.17306
    title: "The First Challenge on Mobile Real-World Image Super-Resolution at NTIRE 2026"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# NTIRE 2026 移动端真实世界图像超分辨率挑战赛

> NTIRE 2026 首次设立移动端真实世界图像超分辨率赛道，要求在 x4 放大因子下恢复高分辨率图像，同时确保模型可在移动设备上高效执行。吸引了 108 支注册队伍，16 支获得有效成绩。

## 核心问题

移动端图像超分辨率面临两难困境：
1. **质量 vs 速度**：高精度模型（如 SwinIR、HAT）计算量巨大，无法在手机端实时运行
2. **真实退化 vs 合成退化**：训练数据多为合成退化（高斯模糊+噪声），但真实场景退化更复杂（压缩伪影、传感器噪声、运动模糊混合）
3. **设备异构性**：不同手机的 SoC 性能差异巨大，需要通用且高效的解决方案

## 挑战赛设计

### 评估指标
- **加权组合**：图像质量评估(IQA)分数 × 加速比(speedup ratio)
- 这一指标同时奖励高画质和高效率，防止"暴力高精度"方案获胜

### 参赛规模
- 108 支注册队伍
- 16 支队伍在最终排名中获得有效成绩
- 挑战赛验证了移动端超分辨率的活跃研究社区

## 关键洞察

1. **移动端模型设计趋势**：轻量化架构（如 ShuffleNet 风格的 SR 网络）正在取代传统的 heavy backbone
2. **x4 放大因子是移动端的甜蜜点**：平衡了视觉质量和计算成本
3. **真实世界退化建模**是关键差异化因素——使用更真实的退化 pipeline 训练的模型在真实场景表现更好

## 为什么重要

移动端图像超分辨率直接影响：
- **手机摄影体验**：变焦拍摄、低光增强等场景需要实时 SR
- **端侧推理优化**：NTIRE 挑战赛推动的轻量化 SR 架构可推广到其他视觉任务
- **NPU 利用率**：SR 是 NPU 的典型工作负载，优化 SR 模型可提升 NPU 利用效率

## 关联
- [[adavfm-adaptive-vfm-edge]] — 自适应视觉基础模型与移动端 SR 的轻量化思路一致
- [[secagent-mobile-gui]] — GUI Agent 的屏幕理解需要高质量图像处理
- [[a-io-adaptive-inference]] — 自适应推理与 SR 的动态质量调节互补
