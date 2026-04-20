---
type: concept
tags: [能效优化, TinyML, 硬件协同设计, LLM推理, 边缘计算, 量化, 调度]
related: [[tinyml-cnn-accelerator-approx-matrix-decomp]], [[aeg-baremetal-ai-acceleration]], [[ggml-llamacpp-hf]], [[mnn-350]], [[kv-cache-quantization-ondevice]]
sources:
  - url: https://arxiv.org/abs/2603.23668
    title: "Energy Efficient Software Hardware CoDesign for Machine Learning: From TinyML to Large Language Models"
    date: 2026-04-04
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# TinyML 到 LLM 的能效软硬件协同设计

> 系统综述从边缘推理到数据中心的能效优化方法，覆盖加速器架构、量化、调度和运行时适配

## 核心问题

AI 的快速扩张带来了严重的可持续性挑战：
- **训练碳排放**：训练单个 LLM 的碳排放相当于多辆乘用车的生命周期排放
- **推理能耗占比**：推理现在占 LLM 全生命周期排放的一半以上（不仅是训练！）
- **边缘设备约束**：数十亿边缘设备必须在严格能耗约束下运行
- **数据移动瓶颈**：能耗越来越受限于数据搬运和内存系统行为，而非算力本身

## 方法架构

综述了从边缘到数据中心的能效协同设计方法：

**覆盖的优化技术栈**：

| 层级 | 技术 |
|------|------|
| 硬件架构 | ASIC/FPGA 数据流、Processing-in-Memory (PIM)、Compute-in-Memory (CIM) |
| 模型优化 | 量化（INT4/INT8/FP8）、剪枝、知识蒸馏 |
| 系统级 | 分区、调度、运行时适配、动态电压频率调节 |
| 编译优化 | 算子融合、内存规划、数据布局优化 |

**关键洞察 — 跨层级共同设计杠杆**：
- 量化 + 定制数据流 + 调度的组合效果远超单独优化
- 边缘和数据中心的最优策略差异巨大（边缘注重延迟/能耗，数据中心注重吞吐/总拥有成本）
- 运行时自适应（根据负载动态调整精度/频率）是被忽视的关键技术

## 关键发现

**重复出现的差距**：
1. **跨平台泛化能力不足**：为特定硬件设计的优化难以迁移到其他平台
2. **协同设计搜索空间过大**：软硬件联合优化的搜索空间爆炸
3. **基准测试不一致**：不同工作使用不同基准和指标，难以公平对比

**分层分解视角**：
提出将优化策略按计算角色（数据搬运、算术计算、控制逻辑）进行分层映射，支持增量适配。

## 为什么重要

- **端到端视角**：首次将 TinyML 到 LLM 的能效优化统一在一个框架下
- **推理碳排放关注**：明确指出推理（而非训练）是主要能耗来源，改变了行业关注点
- **实践指导**：为构建能耗和碳感知的 ML 系统提供了实用指南
- **研究空白识别**：帮助研究者找到最有价值的研究方向

## 关联
- [[tinyml-cnn-accelerator-approx-matrix-decomp]] — TinyML 硬件加速的具体实现
- [[aeg-baremetal-ai-acceleration]] — 硬件直接访问加速方案
- [[kv-cache-quantization-ondevice]] — KV-Cache 量化优化技术
- [[ggml-llamacpp-hf]] — 端侧推理框架的量化实现
- [[mnn-350]] — 阿里端侧推理引擎
