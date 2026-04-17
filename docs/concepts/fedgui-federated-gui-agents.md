---
type: concept
tags: [gui-agent, federated-learning, cross-platform, privacy, benchmark, 分布式训练, 隐私保护]
related: [[clawgui-unified-framework]], [[clawmobile-agentic]], [[cora-mobile-gui-safety]], [[pspa-bench-gui-agent]], [[gui-agent-privacy]], [[comllm-mec-offloading]]
sources:
  - url: https://arxiv.org/abs/2604.14956
    title: "FedGUI: Benchmarking Federated GUI Agents across Heterogeneous Platforms, Devices, and Operating Systems"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# FedGUI: 跨平台联邦 GUI Agent 基准

> 首个覆盖移动/Web/桌面三平台的联邦学习 GUI Agent 基准，解决跨设备、跨操作系统、跨数据源的异构性挑战。arXiv:2604.14956, 2026-04-16.

## 核心问题

传统 GUI Agent 训练依赖集中式数据收集和人工标注，面临两个根本性瓶颈：

1. **高昂的数据成本与有限可扩展性** — 收集涵盖数百个 App、多种设备的 GUI 交互数据极其昂贵
2. **隐私约束导致数据无法共享** — 用户设备上自然产生的大量 GUI 交互数据因隐私原因无法公开传输

现有方案 FedMABench 仅限 Android 用户之间的协作，忽略了跨平台（移动+Web+桌面）协作的巨大潜力，且未考虑设备、操作系统、数据源等多维异构性。

## 方法架构

### 系统设计

FedGUI 遵循标准联邦学习协议，包含一个中央服务器和分布在移动、Web、桌面端的异构客户端。每个客户端在本地数据上训练，仅上传模型参数更新，原始数据永不离开设备。

### 六大数据集

FedGUI 构建了六个数据集以系统研究四类异构性：

| 数据集 | 异构类型 | 数据源 | 客户端数 | 样本数 |
|--------|----------|--------|----------|--------|
| FedGUI-Platform | 跨平台 | AC, GA-W, AS | 3 | 5,400 |
| FedGUI-Device | 跨设备 | 5 种 Android 设备 | 5 | - |
| FedGUI-OS | 跨操作系统 | Ubuntu, macOS, Windows | 3 | - |
| FedGUI-Mobile | 跨数据源 | AC, AitW, GO | 3 | 6,000 |
| FedGUI-Web | 跨数据源 | M2W, GA-W, OA-W | 3 | 1,800 |
| FedGUI-Full | 全部 | 9 个数据源 | 9-36 | 5,400 |

覆盖范围：**900+ 移动应用、40+ 桌面应用、200+ 网站**。

### 统一动作空间

设计了跨平台统一动作空间：定义 6 个平台共享的基础动作（如 CLICK、TYPE），将平台特有动作映射到系统提示中定义的两个独立域。这使跨平台的策略学习和参数聚合成为可能。

### 框架集成

- 支持 **7 种** 联邦学习算法（FedAvg、FedProx、SCAFFOLD、FedYogi、FedAdam、FedAvgM、FedAdagrad）
- 支持 **20+** 基础模型，包括主流开源 VLM 和闭源模型
- 主实验采用 Qwen2-VL-7B + LoRA 以适配资源受限的边缘设备

## 实验结果

### 关键发现 1：跨平台联邦协作的"抢救效应"

单域模型在未见过的平台上**完全失效**（catastrophic failure），但联邦学习即使在严重偏斜的 Source Skew 设定下也能**显著恢复基线性能**。这证明联邦协作对于桥接平台间的领域隔离至关重要——孤立的本地 GUI Agent 跨平台完全不可用。

### 关键发现 2：平台敏感性层级

存在明确的平台敏感性排序：**桌面 > Web > 移动端**。这意味着桌面端从跨平台协作中获益最大，而移动端对异构性的鲁棒性最强。

### 关键发现 3：异构性的破坏性影响

随着数据分布从 IID 覆盖逐渐转向更极端的异构设定，性能持续一致地下降。跨平台异构性从根本上挑战联邦 GUI 学习。

### 各算法在 FedGUI-Platform 上的 Success Rate（%）

| 算法 | AC (IID) | GA-W (Partial) | AS (Skew) | 平均 |
|------|----------|----------------|-----------|------|
| Central (上界) | 48.10 | 53.26 | 60.72 | 54.03 |
| Local (下界) | 27.77 | 35.51 | 28.63 | 30.64 |
| FedAvg | 35.05 | 43.12 | 33.06 | 37.08 |
| FedYogi | 35.81 | 44.38 | 52.28 | 44.16 |
| FedAdam | 37.94 | 43.84 | 53.53 | 45.10 |
| FedAdagrad | 35.81 | 43.12 | 46.75 | 41.89 |

**关键洞察**：优化器类方法（FedYogi、FedAdam）在偏斜分布下表现更鲁棒。中央训练仍是上界，但联邦学习已显著缩小与中央训练的差距（Local 30.64% → FedAdam 45.10%）。

### 效率评估

第 4.7 节评估了通信开销、计算成本和**边缘设备可部署性**，验证了 FedGUI 在真实端侧场景的可行性。

## 关键洞察

1. **隐私与性能的平衡**：FedGUI 证明了在不共享原始数据的前提下，通过联邦协作可以训练出跨平台通用的 GUI Agent，这对移动端隐私保护至关重要
2. **多维度异构性不可忽视**：仅考虑跨平台是不够的——跨设备、跨 OS、跨数据源的异构性各自独立且叠加影响性能
3. **移动平台的天然优势**：移动端在异构环境下表现最稳定，这可能是因为 Android 应用生态相对统一，而 Web 和桌面端的界面多样性更大
4. **LoRA + 边缘部署路径**：FedGUI 用 LoRA 微调 7B 参数模型，验证了在端侧设备上进行 GUI Agent 训练的可行性

## 为什么重要

FedGUI 是手机端 AIOS 生态的关键拼图：

- **隐私保护**：用户 GUI 交互数据永不离开设备，符合端侧隐私的核心要求
- **跨平台泛化**：一个模型同时理解手机 App、网页和桌面软件，而非需要为每个平台单独训练
- **可落地的部署路径**：LoRA 微调 + 边缘设备支持 = 可以在用户的手机上直接参与联邦训练
- **填补关键空白**：这是首个真正覆盖移动/Web/桌面全场景的联邦 GUI Agent 基准

对小米 HyperAI、华为鸿蒙等端侧 AI 系统，FedGUI 提供了训练跨设备通用 Agent 的技术路线参考。用户在小米手机、平板、PC 上的使用数据可以参与联邦训练，产出一个理解所有设备的通用 GUI Agent，而原始数据始终留在本地。

## 关联

- [[clawgui-unified-framework]] — ClawGUI 统一框架关注跨平台 GUI Agent 的动作空间设计，FedGUI 的统一动作空间设计思路有相似之处
- [[clawmobile-agentic]] — ClawMobile 的移动原生 Agent 设计与 FedGUI 中移动端的天然鲁棒性形成互补
- [[cora-mobile-gui-safety]] — CORA 关注 GUI Agent 安全，FedGUI 的隐私保护训练范式是安全保障的另一维度
- [[pspa-bench-gui-agent]] — PSPA-Bench 是 GUI Agent 评测基准，FedGUI 聚焦联邦学习维度的评测
- [[gui-agent-privacy]] — GUI Agent 隐私保护概念页，FedGUI 是联邦学习路线的代表方案
- [[comllm-mec-offloading]] — COMLLM 研究边缘计算卸载，FedGUI 的边缘设备可部署性验证了端侧训练的可行性
