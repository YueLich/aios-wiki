---
type: concept
tags: [端侧训练, 微调, 生物信号, MCU, 可穿戴, 边缘AI, on-device]
related: [[agent-persistent-identity]], [[on-device-inference-memory-pressure]], [[edgecim-hardware-codesign]], [[sustainability-ondevice-intelligence]]
sources:
  - url: https://arxiv.org/abs/2604.13359
    title: "BioTrain: Sub-MB, Sub-50mW On-Device Fine-Tuning for Edge-AI on Biosignals"
    date: 2026-04-18
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# BioTrain: 亚MB级亚50mW端侧微调用于生物信号边缘AI

> 在超低功耗 MCU 上实现 on-device fine-tuning，专用于生物信号处理。来源：arXiv 2604.13359

## 核心问题
在可穿戴设备和医疗 IoT 场景中，模型需要在极低功耗（<50mW）和极小存储（<1MB）的 MCU 上进行端侧微调以适应个体用户。现有 on-device training 方法仍然需要数十MB内存和数百mW功耗，无法在真正的边缘设备上运行。

## 方法/架构
BioTrain 提出三层协同优化：
- **亚MB级模型架构**：精心设计的 tiny backbone，参数量 < 100K
- **极低功耗训练引擎**：针对 ARM Cortex-M 级 MCU 优化的梯度计算
- **生物信号专用**：针对 ECG、EEG、EMG 等时序信号设计的特征提取器

关键技术包括梯度压缩、选择性层微调和定点算术优化，使整个训练过程在 512KB SRAM 内完成。

## 实验结果
- 在 ECG 心律失常检测任务上，端侧微调后准确率提升 8-12%
- 功耗 < 50mW（实测 32mW），适合电池供电设备
- 模型 + 训练状态 < 1MB（实测 780KB）
- 微调时间 < 30秒完成一轮适应

## 关键洞察
BioTrain 证明了端侧训练不仅仅是推理的延伸——它需要完全不同的系统设计。关键在于：(1) 训练和推理共享大部分计算图以减少内存；(2) 梯度计算使用定点而非浮点；(3) 只微调最后一层的少量参数。

## 为什么重要
这是真正的 on-device learning，不是云端训练后部署。对可穿戴健康监测（心率异常、跌倒检测）等场景，端侧微调能实时适应用户生理特征，无需上传敏感健康数据到云端。与 [[agent-persistent-identity]] 的个性化能力相呼应。

## 关联
- [[agent-persistent-identity]] — Agent 持久化身份与端侧个性化
- [[on-device-inference-memory-pressure]] — 端侧训练的内存约束
- [[edgecim-hardware-codesign]] — 边缘硬件协同设计
- [[sustainability-ondevice-intelligence]] — 端侧训练的可持续性考量
