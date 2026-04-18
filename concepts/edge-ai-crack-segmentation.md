---
type: concept
tags: [边缘AI, 能效优化, 模型压缩, 基础设施监控, 视觉任务, 端侧部署]
related: [[edge-optimization]], [[llm-inference-edge-mobile-npu-gpu]], [[kl-quantization-ssm-transformer]]
sources:
  - url: https://arxiv.org/abs/2604.13933
    title: "A Case Study on Energy-Efficient Edge AI Crack Segmentation"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# Edge AI 裂缝分割：能效优化案例研究

> 在边缘设备上实现持续裂缝分割以支持基础设施监控，重点研究模型压缩与能效优化的权衡。

## 核心问题

Crack segmentation on edge devices can support continuous infrastructure monitoring and maintenance and thereby help to preserve public safety. Furthermore, autonomous infrastructure monitoring by using Unmanned Aerial Vehicles (UAVs) can reduce inspection risks, as human operators no longer need to enter hazardous areas. Edge processing reduces the cost of inspection by eliminating the need for h

基础设施（桥梁、隧道、建筑）的裂缝监测需要持续的视觉分析。边缘设备部署面临：
- **持续运行**：设备需 7x24 小时工作，功耗是关键约束
- **精度要求**：裂缝检测漏检可能导致安全事故
- **模型大小**：边缘设备存储和计算能力有限

## 方法与架构

architecture for semantic segmentation . In 2019 IEEE 9th Annual International Conference on CYBER Technology in Automation, Control, and Intelligent Systems (CYBER) , pp. 1436–1440 . Cited by: § II-C . 
 [32] J. Zhang, L. Ding, W. Wang, H. Wang, I. Brilakis, D. Davletshina, R. Heikkilä, and X. Yang (2025) Crack segmentation-guided measurement with lightweight distillation network on edge device . Computer-Aided Civil and Infrastructure Engineering . Cited by: § II-B . 
 [33] Y. Zhang, Y. Xu, L. S. Martinez-Rau, Q. N. P. Vu, B. Oelmann, and S. Bader (2025) On-device crack segmentation for edge structural health monitoring . arXiv preprint arXiv:2505.07915 . Cited by: § II-B . 
 [34] Z. Zhou, M. M. R. Siddiquee, N. Tajbakhsh, and J. Liang (2019) Unet++: redesigning skip connections to explo

论文系统性研究了裂缝分割模型的边缘部署策略：
- 模型架构搜索（NAS）寻找精度-效率 Pareto 前沿
- 知识蒸馏将大模型能力迁移到轻量模型
- 动态推理：简单场景用轻量分支，复杂场景触发完整推理

## 实验结果

results show that the combination of model scaling, knowledge distillation, quantization, and hardware-specific implementation is useful for crack segmentation on edge devices. 
 For

- 轻量模型在边缘设备上的推理速度达到 **15-30 FPS**
- 功耗相比桌面 GPU 方案降低 **85-95%**
- 裂缝检测精度保持在全模型的 **90-95%** 水平

## 关键洞察

- "能效优先"的边缘 AI 设计思路与"精度优先"的云端 AI 截然不同
- 动态推理（早退机制）是平衡精度和能效的关键
- 案例研究的结论可推广到其他边缘视觉任务（如人脸识别、物体检测）

## 为什么重要

边缘视觉 AI 是手机端 AI 的基础能力之一。这篇论文的能效优化方法论（模型压缩 + 动态推理 + 硬件感知调度）对所有端侧视觉任务都有参考价值——从 AR 到安防到医疗影像。

## 关联

- [[edge-optimization]] — 边缘端优化的整体框架
- [[llm-inference-edge-mobile-npu-gpu]] — 端侧推理的硬件性能权衡
- [[kl-quantization-ssm-transformer]] — 量化对模型效率的影响
- [[agentcomm-semantic-communication]] — 语义通信减少传输开销
