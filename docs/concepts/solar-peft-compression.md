---
type: concept
tags: [PEFT, LoRA, 模型压缩, 联邦学习, 边缘部署, 通信效率]
related: [[mobilefinetuner]], [[federated-learning-edge]], [[lora-qlora-edge]], [[edge-cloud-offloading]]
sources:
  - url: https://arxiv.org/abs/2604.08368
    title: "SOLAR: Communication-Efficient Model Adaptation via Subspace-Oriented Latent Adapter Reparametrization"
    date: 2026-04-09
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# SOLAR: PEFT 适配器压缩框架

> 后训练压缩框架，将 LoRA 等 PEFT 适配器的通信成本大幅降低，适用于边缘设备和联邦学习场景。

## 核心问题

LoRA 等 PEFT 方法虽只更新少量参数，但适配器的通信和存储成本仍是资源受限场景的瓶颈。
在联邦学习、边缘部署中，需要频繁传输适配器——如何进一步压缩？

## 方法/架构

SOLAR（Subspace-Oriented Latent Adapter Reparameterization）：
1. 将 PEFT 更新表示为**基础模型奇异向量**形成的基向量的线性组合
2. 加入**受控随机扰动**增加表达能力
3. 利用基础模型与任务特定更新之间的**子空间相似性**（主方向对齐）
4. 将适配器大小与 PEFT 结构解耦，确保紧凑且有表达力

特点：
- **模型无关**：兼容 LoRA、AdaLoRA 及其他适配器模块
- **后训练压缩**：不需要重新训练
- **理论保证**：建立了重构误差的上界

## 实验结果

- 在 LLaMA、GPT、ViT 模型上的语言和视觉任务验证
- 保持任务性能的同时**显著减少模型表示大小**
- 通信效率提升明显，适合分布式系统和边缘设备

## 关键洞察

SOLAR 的核心洞察是：PEFT 更新的主方向与基础模型的奇异向量高度对齐。
这意味着适配器信息是"冗余的"——可以用基础模型已有的方向来表示。
这种子空间压缩思路可推广到任何 PEFT 方法。

## 为什么重要

- **联邦学习关键**：减少每轮通信的适配器大小 = 更快收敛、更低带宽
- **端侧适配**：与 [[mobilefinetuner]] 联合——手机微调后，通过 SOLAR 压缩再上传
- **通用性**：不绑定特定 PEFT 方法，覆盖面广

## 关联
- [[mobilefinetuner]] — MobileFineTuner 做端侧微调，SOLAR 压缩适配器降低通信成本
- [[federated-learning-edge]] — 联邦学习中适配器传输的效率瓶颈
- [[lora-qlora-edge]] — LoRA 是 SOLAR 的主要压缩目标
- [[edge-cloud-offloading]] — 端云协同中，压缩适配器减少上传数据量
