---
type: concept
tags: [端侧微调, 移动端, LLM, fine-tuning, PEFT, privacy, on-device-training]
related: [[mobilellm-pro]], [[solar-peft-compression]], [[gemma3]], [[qwen25]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2512.08211
    title: "MobileFineTuner: A Unified End-to-End Framework for Fine-Tuning LLMs on Mobile Phones"
    date: 2025-12-12
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# MobileFineTuner

> 首个开源端到端框架，实现在真实手机上直接微调 LLM。来自昆山杜克大学和香港大学。

## 核心问题

高质量公开数据正在枯竭（预计2026-2032年耗尽），但手机端产生了海量私有用户数据。
现有微调方案主要基于仿真环境或依赖 IoT 设备/PC，普通手机几乎未被探索。
关键缺口：缺乏一个能在手机上实际运行的 LLM 微调开源框架。

## 方法/架构

MobileFineTuner 是统一的开源框架，支持：
- **全参数微调（Full-FT）** 和 **参数高效微调（PEFT）**
- 系统级优化三大核心：
  1. **参数分片（Parameter Sharding）**：将模型参数分片存储，突破手机内存限制
  2. **梯度累积（Gradient Accumulation）**：用时间换空间，减少显存峰值
  3. **能量感知计算调度（Energy-Aware Scheduling）**：根据电池状态动态调整计算强度

已在真实手机上微调 **GPT-2、Gemma 3、Qwen 2.5**，验证可行性。

## 实验结果

- 在真实手机端完成端到端微调流程（非仿真）
- 消融实验验证了三项系统优化的有效性
- 支持从轻量级（GPT-2）到中型（Gemma 3, Qwen 2.5）多种模型
- 框架开源，可复现

## 关键洞察

这不仅是工程实现，更是方向性突破——证明手机端微调从"不可能"变为"可行"。
私有数据微调 + 本地执行 = 完整的隐私保护 AI 闭环。
手机是最普及的终端设备，这个框架降低了端侧个性化 AI 的门槛。

## 为什么重要

- **隐私保护**：用户数据不离开设备，利用私有数据微调
- **数据枯竭应对**：当公开数据用尽时，私有数据是新的增长点
- **普及性**：手机是最广泛的计算平台，人人可用
- **生态意义**：与 [[mobilellm-pro]]（推理）互补——推理在端侧已成熟，微调是下一环

## 关联
- [[mobilellm-pro]] — MobileLLM-Pro 提供端侧推理，MobileFineTuner 提供端侧训练，二者互补
- [[solar-peft-compression]] — SOLAR 压缩 PEFT 适配器，可与 MobileFineTuner 联合降低通信开销
- [[gemma3]] — 被微调的目标模型之一
- [[qwen25]] — 被微调的目标模型之一
- [[on-device-inference-memory-pressure]] — 端侧推理的内存压力与 MobileFineTuner 的参数分片方案呼应
- [[edge-cloud-offloading]] — 端侧微调 vs 云端微调的权衡
