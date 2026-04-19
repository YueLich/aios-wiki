---
type: concept
tags: [on-device-learning, mcu, monocular-depth, ultra-low-power, iot, continual-learning]
related: [[biotrain-ondevice-finetuning-mcu]], [[ahc-mcu-continual-detection]], [[visionclaw-wearable-agent]]
sources:
  - url: https://arxiv.org/abs/2512.00086
    title: "Multi-modal On-Device Learning for Monocular Depth Estimation on Ultra-low-power MCUs"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# 多模态端侧学习：超低功耗 MCU 上的单目深度估计

> 在 RISC-V MCU（<100mW）上实现多模态端侧学习，让微型 IoT 设备具备空间感知能力

## 核心问题

新一代微型空间感知 IoT 设备（掌上纳米无人机、MR 眼镜、智能摄像头）正在快速发展。这些设备搭载超低功耗（ULP）处理器，需要实时运行 AI 算法分析传感器数据。

单目深度估计（MDE）是关键任务——用单个廉价摄像头传感器提取场景深度信息。但传统方案面临两难：
- **云端推理**：延迟高、隐私风险、需持续网络连接——不适合微型无人机等离线场景
- **预训练静态模型**：无法适应新环境（光照变化、新场景），在 MCU 上精度受限

## 方法/架构

论文提出在 ULP MCU 上实现**多模态端侧学习**的方法：

1. **多模态输入融合**：结合视觉（摄像头）和其他传感器信号（如 IMU、距离传感器），在 MCU 上进行融合
2. **端侧微调**：利用设备在部署环境中收集的数据，对预训练模型进行在线微调
3. **轻量化架构**：针对 MCU 的内存和计算约束设计专用网络结构
4. **能量感知调度**：根据设备能量状态动态调整推理/学习的计算量

## 关键洞察

1. **端侧学习 vs 端侧推理**的区别：端侧推理只是在设备上运行固定模型；端侧学习允许模型适应新环境。在 ULP MCU 上实现端侧学习是一个重大突破，因为 MCU 的计算资源极其有限。

2. **多模态是关键**：单目摄像头的深度估计固有歧义，多模态融合（如 IMU 提供的运动信息）可以显著提升精度，且额外传感器的功耗增加很小。

3. **持续适应的价值**：IoT 设备通常长期部署在变化环境中（如无人机从室内飞到室外）。端侧学习让模型持续适应，而非依赖一次性预训练。

## 为什么重要

- **IoT 设备的"眼睛"**：深度估计是空间感知的基础，让 IoT 设备从"被动感知"升级为"主动理解"
- **超低功耗约束的突破**：在 <100mW 的 MCU 上实现端侧学习，为更多端侧学习应用开辟道路
- **隐私保护**：数据不出设备，在医疗、家庭监控等隐私敏感场景中至关重要
- **与手机端 AIOS 的关联**：手机的传感器阵列（摄像头 + IMU + ToF）远强于 MCU，论文的方法论可以迁移到手机端，实现更高效的端侧空间理解

## 关联

- [[biotrain-ondevice-finetuning-mcu]] — 同样在 MCU 上实现端侧微调，但目标是生物信号而非视觉
- [[ahc-mcu-continual-detection]] — MCU 上的持续学习异常检测，与端侧学习理念一致
- [[visionclaw-wearable-agent]] — 可穿戴设备上的视觉 Agent，深度估计是其感知基础
- [[edgeflow-cold-start]] — 端侧模型冷启动优化，与端侧学习的模型初始化相关
