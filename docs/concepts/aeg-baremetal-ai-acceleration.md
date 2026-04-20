---
type: concept
tags: [AI加速器, Baremetal, 异构计算, 边缘推理, 硬件抽象, RTOS替代]
related: [[tinyml-cnn-accelerator-approx-matrix-decomp]], [[energy-efficient-sw-hw-codesign-tinyml]], [[edgecim-hardware-codesign]]
sources:
  - url: https://arxiv.org/abs/2604.09565
    title: "AEG: A Baremetal Framework for AI Acceleration via Direct Hardware Access in Heterogeneous Accelerators"
    date: 2026-04-13
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# AEG: 裸机 AI 加速框架

> 通过直接硬件访问绕过操作系统开销，在异构加速器上实现高性能端侧 ML 推理

## 核心问题

边缘系统部署 AI 推理的需求日益增长（低延迟、高能效），但现有框架存在根本瓶颈：
- **操作系统开销**：TVM、嵌入式 ML 运行时等框架假设 OS 中介执行环境，引入内核交叉、调度延迟、内存子系统开销
- **RTOS 复杂性**：TinyML 框架依赖实时操作系统（RTOS），引入不必要的复杂性和性能瓶颈
- **可移植性 vs 性能矛盾**：OS 抽象提高可移植性但牺牲性能

以 AMD Versal ACAP（集成 AIE 向量处理器阵列）为例：硬件提供高吞吐能力，但软件栈成为瓶颈。

## 方法架构

**"Control as Data" 范式**：
核心创新是将复杂控制逻辑展平为线性可执行的**运行时控制块（RCB）**：

1. **运行时硬件抽象层（RHAL）**：最小化硬件抽象，避免 OS 介入
2. **RCB 机制**：将高级模型（ADF 图）转换为线性执行序列
3. **运行时平台管理（RTPM）**：处理系统级资源管理
4. **运行时平台监控（RTPMon）**：监控加速器状态

**架构设计**：
- 运行时与硬件细节完全解耦
- 通用引擎通过 RHAL 驱动不同加速器
- 支持 AIE 阵列的直接编程访问

## 关键洞察

**为什么重要**：
- **性能天花板突破**：消除 OS 开销意味着接近硬件理论峰值的推理性能
- **异构计算统一**：单一框架覆盖 AI Engine、GPU、NPU 等异构加速器
- **延迟关键应用**：对于毫秒级延迟要求的应用（实时目标检测、语音唤醒），OS 开销可能是性能瓶颈
- **端侧推理新范式**：证明了"裸机推理"的可行性和优势

**深层分析**：
- 这种方法特别适合确定性延迟要求的场景（如安全关键系统）
- "Control as Data" 概念借鉴了数据流计算的思想，将控制流转换为数据流
- 对比 TinyML 生态（TensorFlow Lite Micro 等依赖 RTOS），AEG 提供了更激进但更高效的替代方案

## 关联
- [[tinyml-cnn-accelerator-approx-matrix-decomp]] — 另一种硬件加速路径
- [[energy-efficient-sw-hw-codesign-tinyml]] — 软硬件协同设计综述
- [[edgecim-hardware-codesign]] — 边缘硬件协同设计
