---
type: concept
tags: [vision-foundation-model, edge-intelligence, on-device, adaptive-inference, NAS, always-on, smart-glasses]
related: [[edgeflow-cold-start]], [[visionclaw-wearable-agent]], [[coremltools-9]], [[gemma4-ondevice]], [[mnn-350]]
sources:
  - url: https://arxiv.org/abs/2604.15622
    title: "AdaVFM: Adaptive Vision Foundation Models for Edge Intelligence via LLM-Guided Execution"
    date: 2026-04-17
    reliability: high
  - url: https://arxiv.org/html/2604.15622v1
    title: "AdaVFM Full Paper HTML"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# AdaVFM: 自适应视觉基础模型的边缘智能推理

> CMU 与 Meta 联合提出的边缘端自适应视觉推理框架，通过 NAS + 云端 LLM Agent 实现动态子网选择，在智能眼镜等设备上实现始终在线的多模态感知。

## 核心问题

语言对齐的视觉基础模型（VFM，如 CLIP/DINOv2）在零样本分类、开放词汇分割等任务上表现出色，但其大规模参数量和高计算需求使其难以在边缘设备上部署。传统的做法是使用单一的轻量化模型，但实验表明：

- **任务复杂度决定模型需求**：简单任务（如 9 类 ADE20K 分割）用 50M 模型即可，但 150 类复杂任务需要 300M 模型
- **固定模型 = 固定浪费**：始终使用大模型在简单场景浪费算力，始终使用小模型在复杂场景精度不足
- **上下文信息被忽视**：场景语义（如"在驾驶"）能帮助缩小目标范围，但现有系统无法利用

## 方法/架构

AdaVFM 采用**端云协同的双组件架构**：

### 1. 边端自适应视觉编码器
- 基于 ConvNeXt-v2 架构，通过 NAS 搜索空间暴露多个子网路径
- **5 个代表子网**（从 Tiny 到 Large）：
  - Min: 6.2M 参数, 1.29G FLOPs, 25ms 延迟, 1.2mJ 能耗
  - Tiny: 16.1M 参数, 2.86G FLOPs, 52ms, 2.4mJ
  - Small: 28.7M 参数, 5.05G FLOPs, 89ms, 4.1mJ
  - Base: 35.9M 参数, 6.46G FLOPs, 120ms, 5.5mJ
  - Large: 50.3M 参数, 9.28G FLOPs, 182ms, 8.4mJ
- 运行时根据云端指令动态切换子网，实现在 ARM Ethos-U55 NPU（7nm FinFET）上的部署
- 持续处理每一帧，计算视觉嵌入与文本嵌入的余弦相似度

### 2. 云端多模态 LLM 推理 Agent
- **低频调用**：接收稀疏的时间采样图像和用户文本交互
- 场景理解：推断上下文（如"驾驶中"→ 关注车辆、行人、标志）
- **双输出**：
  - 生成选定开放词汇概念的文本嵌入
  - 推荐边端执行方案（选择哪个子网）
- 利用增强的模型元数据（各子网的性能特征）做出决策

### 训练管线
- **两阶段训练**：
  1. NAS 集成的 VFM 蒸馏：从大模型蒸馏到可搜索的子网空间
  2. 视觉-文本对齐：确保子网输出与语言嵌入空间兼容
- 支持开放词汇使用场景，无需预定义类别

## 实验结果

### 零样本分类（对比 SOTA）
| 方法 | IN1K Acc@1 | Food-101 | Cal101 | Pets | 参数量 | 延迟 |
|------|-----------|----------|--------|------|--------|------|
| CLIP ViT-B | 68.3 | 83.4 | 89.1 | 86.4 | 86M | 423ms |
| DINO.txt ViT-L | 82.3 | 93.8 | 97.2 | 96.3 | 304M | 1119ms |
| **AdaVFM (最优)** | **+7.9%** over 同规模 | - | - | - | **50M** | **182ms** |

- AdaVFM 在同等规模模型上 IN1K 准确率提升 7.9%，ADE20K mIoU 提升 5.2%
- 相比同精度模型，FLOPs 降低最多 77.9%
- 硬件实测：比 ViT-B 基线延迟低 2.3x，能耗低 2.4x

### 关键发现
- **简单 vs 复杂任务的精度落差**：DINOv2 ViT-S 在简单数据集（Cal101: -0.6, Pets: -1.6）与 ViT-g 几乎无差距，但在 IN1K 上差距 -4.4
- **开放词汇分割中的任务感知**：50M 和 300M 模型在 9 类粗粒度分割上表现相近，但在 150 类精细分割上差距显著
- **NAS 子网的连续谱**：通过子网插值实现了从 6.2M 到 50.3M 的平滑精度-效率权衡

## 关键洞察

1. **"一刀切"在边缘端行不通**：传统方法选择一个固定大小的模型部署，AdaVFM 证明动态子网选择能同时满足简单场景的低功耗需求和复杂场景的高精度需求

2. **云端 Agent 以极低成本赋能边缘**：LLM Agent 只需低频调用（处理稀疏采样），却能显著提升边端效率。这是端云协同的精妙设计——不是把所有推理放在云端，而是让云端做"决策"、边端做"执行"

3. **NAS 不只是离线优化**：将 NAS 集成到运行时框架中，使模型架构搜索的成果能在推理时动态利用，而非只在部署时选择一个固定子网

4. **与 VisionClaw 的互补关系**：VisionClaw 解决了"感知+行动"的 Agent 架构问题，AdaVFM 解决了"高效感知"的底层推理问题。两者结合才能实现真正实用的始终在线智能眼镜

## 为什么重要

- **智能眼镜/可穿戴设备的核心瓶颈**：视觉推理是始终在线 AI 的最大能耗来源，AdaVFM 提供了从 6.2M 到 50.3M 的自适应调度能力，使 1-8mJ 级推理成为可能
- **开放词汇 ≠ 固定类别**：支持任意文本查询的零样本视觉理解，这对移动场景（用户可能问任何问题）至关重要
- **NPU 利用率优化**：在 ARM Ethos-U55 NPU 上实测验证，意味着该方案可直接部署到现有手机/眼镜芯片
- **端云协同范式的推进**：不是简单的模型压缩或知识蒸馏，而是用云端 Agent 做运行时决策，代表了边缘 AI 架构的新方向

## 关联
- [[edgeflow-cold-start]] — 同样关注边缘端 LLM/VFM 的高效启动与推理
- [[visionclaw-wearable-agent]] — VisionClaw 是 Agent 层的可穿戴智能方案，AdaVFM 是底层视觉推理的高效方案，两者互补
- [[gemma4-ondevice]] — Gemma 4 代表了端侧语言模型的能力上限，AdaVFM 代表端侧视觉模型的自适应推理
- [[mnn-350]] — MNN 是端侧推理引擎，AdaVFM 的 NAS 子网调度需要类似引擎的支持
- [[coremltools-9]] — Apple 端侧部署工具链，AdaVFM 的自适应框架可与 CoreML 的模型选择机制结合
