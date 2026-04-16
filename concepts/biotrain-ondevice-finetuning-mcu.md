---
type: concept
tags: [on-device-finetuning, compiler, MCU, wearable, biosignal, backpropagation, optimization, edge-ai]
related: [[lcsb-finetuning-ondevice]], [[edgeflow-cold-start]], [[sustainability-ondevice-intelligence]], [[ahc-mcu-continual-detection]], [[sense-less-infer-more]]
sources:
  - url: https://arxiv.org/abs/2604.13359
    title: "BioTrain: Sub-MB, Sub-50mW On-Device Fine-Tuning for Edge-AI on Biosignals"
    date: 2026-04-17
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# BioTrain: MCU 上的全网络反向传播训练框架

> 编译器辅助的端侧训练框架，在 50mW 功耗包络内实现 MCU 全网络反向传播，8× 峰值内存压缩，EEG 上最高提升 35% 准确率。

## 核心问题

可穿戴生物信号（EEG、EOG 等）存在严重的跨被试和跨会话分布漂移——电极-皮肤阻抗波动、出汗、传感器位移等因素导致云端训练的模型部署后性能急剧下降。传统解决方案要么仅做线性探针（LP，只更新最后一层），要么在 MCU 上根本无法运行全网络反向传播（BP）——GAP9 MCU 仅 1.5MB L2 内存，标准全微调需要 ~5.4MB 峰值激活内存，超出容量 3.6 倍。

**关键矛盾**：线性探针不足以应对大幅信号变化（文献 [4] 证实），但全 BP 的内存和计算需求远超穿戴设备的资源上限。

## 方法/架构

BioTrain 基于 Deeploy 编译器（专为 MCU 能效推理设计），将其扩展到训练工作负载：

### 三组件架构

1. **PULPTrainLib 集成**：接入优化的 CNN 梯度内核，支持分块（tiling）计算
2. **静态内存分配与分块**：利用 Deeploy 的静态内存管理机制，将梯度计算分块到片上 L2 内存
3. **Mini-batch 网络拓扑修改**：修改基线 CNN 架构以支持片上 mini-batch 处理

### 关键技术

- **Edge-FT（边缘全微调）**：全网络 BP，但通过编译器级的内存分块将峰值激活压缩到 0.67MB
- 对比 Full-FT（标准全微调，需 5.4MB）：8× 内存压缩
- 对比 LP（线性探针，0.19MB）：训练参数从 0.07k 扩展到 7.9k

### 硬件平台

GAP9 MCU（GreenWaves Technologies）：
- 1.5MB L2 片上内存
- RISC-V 多核架构
- FP32 计算

## 实验结果

### 两个真实场景

| 场景 | 说明 |
|------|------|
| Day-1 新用户校准 | 新用户首次使用时的即时模型个性化 |
| 纵向自适应 | 长期使用中的持续信号漂移适应 |

### 定量结果（Table IV 完整数据）

| 数据集 | 策略 | 准确率 (Subj/Sess) | 参数量 | FLOPs | L2 峰值内存 (MB) | 延迟 (ms) | 功耗 (mW) | 吞吐量 (GFLOPs/s) |
|--------|------|-------------------|--------|-------|-----------------|----------|----------|-------------------|
| EEG | LP | 74.8% / 76.2% | 0.07k | 139.2M | 0.19 | 360.0 | 45.2 | 0.38 |
| EEG | Full-FT | 80.0% / 78.7% | 7.9k | 416.8M | 5.36 † | — | — | — |
| EEG | **Edge-FT** | **86.4% / 83.9%** | 7.9k | 416.8M | **0.67** | 469.6 | 43.8 | 0.89 |
| EOG | LP | 83.3% / 86.5% | 0.2k | 7.2M | 0.11 | 34.4 | 50.4 | 0.21 |
| EOG | Full-FT | 88.7% / 89.1% | 4.1k | 20.8M | 2.24 † | — | — | — |
| EOG | **Edge-FT** | **87.7% / 87.2%** | 4.1k | 20.8M | **0.28** | 93.6 | 48.2 | 0.22 |

† 超出 GAP9 L2 容量（1.5MB），无法完全在片上执行

### 核心数据

- **EEG 准确率提升**：Edge-FT 86.4% vs LP 74.8% → **+11.6 个百分点**（Day-1），比 Full-FT 还高 6.4pp
- **EOG 准确率**：Edge-FT 87.7% 接近 Full-FT 88.7%，但后者超出内存无法实际运行
- **功耗**：EEG 43.8mW，EOG 48.2mW，均在 50mW 包络内
- **续航实测**：320mAh 电池支持 ~211 次 EEG 或 ~951 次完整训练会话（每会话 40 epoch × 200 样本）
- **吞吐量**：EEG 17 samples/s，EOG 85 samples/s

### 纵向自适应结果

Edge-FT 在纵向漂移场景下表现最稳定：
- EEG：S₂ 开始稳定在 84.8%，S₄ 维持 85.8%（LP 在 S₂→S₄ 有明显下降）
- EOG：87.2%，与 Full-FT（89.1%）可比
- 避免了 LP 和其他方法观察到的"自适应滞后"现象

## 关键洞察

1. **编译器级优化 > 运行时技巧**：BioTrain 的突破不在算法层面（仍用标准 BP），而在编译器层面——通过静态内存分块将 5.4MB 压缩到 0.67MB。这说明端侧训练的瓶颈更多是系统工程而非理论问题。

2. **全网络 BP 在 MCU 上可行**：传统观点认为 MCU 只能做 LP 或最后一层微调。BioTrain 证明在 1.5MB L2 的 GAP9 上，7.9k 参数的全网络 BP 完全可行，且性能显著优于 LP。

3. **穿戴设备的训练续航被严重低估**：211 次 EEG 训练会话意味着用户每天校准一次，可以持续 ~7 个月。这打开了"持续个性化"的产品可能性。

4. **对手机端 AI 的启示**：虽然 BioTrain 针对 MCU，但其编译器级内存分块思想可以迁移到手机端 NPU/ISP 上的端侧微调。手机有更大的内存（8-16GB）但功耗约束类似。

## 为什么重要

BioTrain 是端侧训练领域的一个里程碑——它证明了在**最极端的硬件约束**（MCU、1.5MB 内存、50mW 功耗）下，全网络反向传播不仅是理论可行的，而且是**实际可用的**（续航 7 个月）。这对手机端 AIOS 的意义在于：

- **端侧个性化不再需要云端**：从 MCU 到手机，全栈端侧训练成为可能
- **编译器是端侧 AI 的核心竞争力**：MNN、TFLite 等推理框架需要向训练扩展
- **生物信号 = 下一代手机输入**：EEG/EOG 的端侧处理可能成为 AR/VR、健康监测的标准功能

## 关联

- [[lcsb-finetuning-ondevice]] — LCSB 也做端侧 LLM 微调，但针对手机端大模型，BioTrain 针对 MCU 小模型
- [[edgeflow-cold-start]] — EdgeFlow 优化端侧 LLM 冷启动，BioTrain 优化端侧训练冷启动（Day-1 校准）
- [[sustainability-ondevice-intelligence]] — BioTrain 的能效数据（43.8mW）直接支持可持续性分析
- [[ahc-mcu-continual-detection]] — AHC 也在 MCU 上做持续学习，但用的是压缩而非全 BP
- [[sense-less-infer-more]] — 同样关注边缘医疗 AI，但侧重推理而非训练
