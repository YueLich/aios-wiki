---
type: entity
tags: [multimodal, mobile, LMM, on-device, Snapdragon, inference, efficient-ai, edge-ai]
related: [[gemma4-ondevice]], [[minicpm-242]], [[edgedit]]
sources:
  - url: https://arxiv.org/abs/2405.12107
    title: "Imp: Highly Capable Large Multimodal Models for Mobile Devices"
    date: 2024-05-20
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Imp: 面向移动设备的高性能大型多模态模型

> 在手机端实现 13 tokens/s 推理速度的多模态大模型，性能超越同规模和 13B 级别竞品

## 核心问题

现有大型多模态模型（LMM）虽然在开放世界多模态理解方面表现出色，但通常参数量大、计算密集，在资源受限场景中难以应用。已有的轻量级 LMM（如 TinyLLaVA 系列）虽然将规模压缩到 3B 左右，但在能力上仍有显著差距。

## 方法/架构

Imp 提出了一套系统的移动端 LMM 优化方法：

- **模型架构**：在不使用任何专有预训练模型或私有数据的情况下，通过精心的架构设计和训练策略，构建高效的多模态模型
- **视觉编码器优化**：针对移动端推理特点优化视觉编码器，降低图像处理的计算开销
- **语言模型压缩**：对 LLM backbone 进行结构化压缩，适配 Snapdragon NPU 的计算特性
- **端到端优化**：使用 Qualcomm AI Runtime 进行模型编译和推理优化

## 实验结果

- **Imp-3B 模型**在 Qualcomm Snapdragon 8Gen3 上实现约 **13 tokens/s** 的推理速度
- 在广泛的 LMM 基准测试中，**超越同规模的其他模型**
- 在 13B 级别模型中也表现出竞争力，**持续超越当时的 SOTA LMM**
- 完全开源：代码和预训练模型公开可用

## 关键洞察

Imp 的核心价值在于证明了：**端侧多模态模型不需要在能力上做根本妥协**。通过架构创新和系统级优化，3B 参数的模型可以在手机上流畅运行多模态理解任务。这打破了"端侧=低能力"的固有认知。

特别值得注意的是，Imp 不依赖任何专有组件——这对于开源生态和社区发展具有重要意义。

## 为什么重要

- **端侧多模态成为现实**：Imp 证明手机可以运行实用的多模态 AI（图像理解、视觉问答等）
- **对移动 AI 生态的影响**：
  - 小米 HyperAI、华为 HarmonyOS 等平台可参考 Imp 的架构设计
  - 为手机厂商自研端侧多模态能力提供了技术路线参考
- **开源标杆**：完全开源的 3B 端侧多模态模型，降低了相关研究的门槛
- **骁龙 8Gen3 充分利用**：展示了在当前旗舰手机芯片上的实际推理能力

## 关联
- [[gemma4-ondevice]] — Google 的端侧多模态方案
- [[minicpm-242]] — 面壁智能的端侧小模型
- [[edgedit]] — 端侧图像生成方案
- [[coremltools-9]] — Apple 端侧推理优化工具链
