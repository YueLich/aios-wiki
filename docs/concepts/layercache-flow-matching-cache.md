---
type: concept
tags: [推理优化, Flow Matching, 缓存, DiT, 推理加速, diffusion, 图像生成, layer-cache]
related: [[on-device-inference-memory-pressure]], [[edge-inference-memory-pressure]], [[ggml-llamacpp-hf]], [[mnn-350]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.16492
    title: "LayerCache: Exploiting Layer-wise Velocity Heterogeneity for Efficient Flow Matching"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# LayerCache: 层级缓存加速 Flow Matching

> 利用 DiT 模型各层"速度"异质性的智能缓存策略，在 Flow Matching 图像生成中实现 1.5-2.8x 加速，仅损失 <1% 质量。

## 核心问题

Flow Matching 已成为图像生成的主流范式（FLUX、Qwen-Image、Stable Diffusion 3 均基于 DiT 架构）。但 DiT 模型的推理计算代价极高——60 层 Transformer 需要在每个去噪步中全部执行。现有缓存方法（如 TeaCache）采用粗粒度的全局缓存策略，无法精准处理各层的不同行为。

**关键观察**：DiT 模型各层的"速度变化率"（velocity change rate Δ^g(t)）存在显著异质性：
- **浅层**：极其稳定，98% 的时间步可安全缓存
- **中间层**：变化中等，约 58% 可缓存
- **深层**：偶发尖峰（sporadic spikes），缓存会产生质量灾难

## 方法/架构

LayerCache 提出 **3D 调度策略**（3D Schedule），在（时间步, 层组, 频率）三个维度上分配固定计算预算：

1. **层分组（Layer Grouping）**：根据 velocity 异质性将 60 层分为浅/中/深三组
2. **时间步调度（Timestep Schedule）**：在不同去噪阶段动态调整缓存比例
3. **频率调度（Frequency Schedule）**：对深层偶尔安全的时间步也可缓存

系统维护一个固定计算预算 C，通过优化求解最优的 3D 缓存分配方案。

**关键技术**：
- 利用 velocity 变化率作为"缓存安全信号"
- 深层的尖峰检测机制（spike detection）避免质量退化
- 不依赖额外训练，纯推理时优化

## 实验结果

在 Qwen-Image（60 层 DiT, 50 去噪步, 1024x1024）上：

| 方法 | 加速比 | FID↓ | LPIPS↓ |
|------|--------|------|--------|
| 基线（无缓存） | 1.0x | — | — |
| TokenCache | 1.8x | +2.3 | +0.015 |
| StepCache | 2.0x | +3.1 | +0.022 |
| **LayerCache** | **2.4x** | **+0.4** | **+0.003** |
| LayerCache (激进) | **2.8x** | +1.2 | +0.008 |

在 FID 和 LPIPS 指标上，LayerCache 在同等加速比下显著优于所有基线方法。

## 关键洞察

1. **层异质性是可利用的结构特性**：不是所有层都需要相同频率的计算。浅层的稳定性使得它们可以被大幅跳过，而深层的偶发尖峰需要保留。
2. **固定预算比自适应阈值更稳定**：预定义的 3D 调度避免了自适应方法的不稳定性。
3. **对端侧推理的启示**：LayerCache 的思想可以推广到其他 Transformer 架构（如 LLM 的 KV-Cache 优化），对移动端推理框架（如 [[ggml-llamacpp-hf]]、[[mnn-350]]）有直接参考价值。
4. **与量化互补**：层缓存与量化是正交优化手段，可以叠加使用。

## 为什么重要

- **对移动端图像生成**：在 Snapdragon/Mali GPU 上运行 Stable Diffusion 等模型时，2-3x 加速意味着实时生成成为可能
- **对通用推理优化**：层异质性分析的方法论可以应用于 LLM 推理的 KV-Cache 策略
- **对边缘设备**：固定计算预算的方法天然适合资源受限场景（不需要动态自适应的额外开销）

## 关联
- [[on-device-inference-memory-pressure]] — 缓存策略直接减少内存压力
- [[kv-cache-quantization-ondevice]] — 与 KV-Cache 量化互补的缓存优化
- [[ggml-llamacpp-hf]] — llama.cpp 可借鉴的层缓存策略
- [[mnn-350]] — MNN 推理引擎的优化参考
- [[edgeflow-cold-start]] — 推理优化的不同维度
