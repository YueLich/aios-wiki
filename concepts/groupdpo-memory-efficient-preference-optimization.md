---
type: concept
tags: [optimization, training, dpo, memory-efficiency, fine-tuning, 端侧训练]
related: [[triton-dispatch-ragged-attention]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.15602
    title: "GroupDPO: Memory efficient Group-wise Direct Preference Optimization"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# GroupDPO: 内存高效的群组偏好优化

> 通过解耦样本反向传播，大幅降低群组偏好优化的峰值内存，使其可扩展到更大规模。来自 Jixuan Leng 等人 (arXiv 2604.15602)。

## 核心问题

偏好优化（如 DPO）广泛用于对齐 LLM 与人类偏好，但现有方法通常每个 prompt 只用一个正-负样本对，浪费了偏好数据集中可用的额外监督信号。近期的群组偏好优化虽然尝试联合对比多个响应，但群组耦合目标的内存开销使其可扩展性未被充分探索。

## 方法/架构

**GroupDPO** 的核心创新：
- **梯度保持 + 样本解耦**：在反向传播过程中解耦样本，保留梯度信息的同时大幅降低峰值内存
- **群组对比**：每个 prompt 使用多个候选响应进行联合偏好学习，充分利用数据集中的监督信号
- **可扩展性**：内存优化使其能够在有限 GPU 内存下处理更大的群组规模

## 实验结果

- 峰值内存使用相比标准群组 DPO 显著降低
- 在对齐质量上保持或超越单对 DPO 方法
- 可扩展到更大群组规模，充分利用偏好数据

## 关键洞察

对于端侧微调场景，内存效率是核心瓶颈。GroupDPO 的"梯度保持 + 样本解耦"思路可推广到其他端侧训练场景：
- 在手机 NPU 上进行小规模偏好微调
- 设备端 RLHF 的内存优化
- 与 [[kv-cache-quantization-ondevice]] 类似的低精度训练策略

## 为什么重要

- **端侧微调可行性**：GroupDPO 降低了偏好优化的内存门槛，使设备端个性化对齐成为可能
- **数据效率**：充分利用每个 prompt 的多个响应，减少所需的 prompt 数量
- **与量化互补**：可与 FP16/INT8 量化结合，进一步降低端侧训练内存需求

## 关联
- [[triton-dispatch-ragged-attention]] — 推理优化，与 GroupDPO 训练优化互补
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化，类似内存优化方向
- [[peft]] — 参数高效微调，GroupDPO 可与其结合
