---
type: concept
tags: [端云协同, 推理优化, 边缘计算, 语义压缩, 通信优化]
related: [[edge-cloud-offloading]], [[micro-language-models-edge]], [[comllm-mec-offloading]], [[wisv-device-edge-speculative-decoding]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://arxiv.org/abs/2604.19623
    title: "SAGE: Training-Free Semantic Evidence Composition for Edge-Cloud Inference under Hard Uplink Budgets"
    date: 2026-04-22
    reliability: medium
created: 2026-04-22
updated: 2026-04-22
---

# SAGE: 硬上行预算下的端云推理语义证据合成

> 在端云混合推理中，上行信道对传输比特数有硬约束。SAGE 证明基于注意力重要性的传输选择本质上受限，并提出训练无关的语义证据合成方法。来源：arXiv 2604.19623

## 核心问题

端云混合推理将困难输入卸载到远程大模型，但上行信道（设备→云）对每个请求的传输比特数有硬约束。**标准做法**是基于注意力权重选择最重要的 token/特征传输，但这在硬预算下效果有限。

**关键发现**：
1. 用低重要性但**互补**的单元替换高重要性单元，反而能提升服务器准确率——说明注意力重要性不等于信息增益
2. 传输内容应该基于**语义互补性**而非单一的重要性度量

## 方法/架构

### SAGE 框架

**训练无关（Training-Free）**的设计意味着：
- 不需要重新训练端侧或云侧模型
- 即插即用，适用于已部署的端云推理系统

**核心机制**：
- **语义证据合成**：将端侧生成的中间表示组织为"语义证据"，而非简单地选择高注意力 token
- **互补性优化**：在硬上行预算约束下，最大化传输内容对云侧推理的信息增益
- **预算感知编排**：根据信道可用带宽动态调整传输策略

### 与传统方法对比

| 方案 | 选择策略 | 硬预算下性能 | 训练需求 |
|------|---------|------------|---------|
| 注意力重要性 | Top-K 注意力 | 受限 | 无 |
| 学习型压缩 | 训练编码器 | 较好 | 需要 |
| **SAGE** | **语义互补性** | **最优** | **无** |

## 为什么重要

- **端云推理的通信瓶颈**：在移动网络中，上行带宽通常是下行的 1/5-1/10，SAGE 专门解决这个不对称瓶颈
- **与 [[micro-language-models-edge]] 的互补**：μLM 解决"感知延迟"，SAGE 解决"传输效率"，两者结合可实现极致的端云协同
- **训练无关设计的工程价值**：不需要修改现有模型，可直接集成到 [[mnn-350]]、Core ML 等推理框架

## 关键洞察

- **注意力不等于信息量**：高注意力权重的 token 可能已经被端侧模型处理得很好，低注意力但"云侧需要"的 token 才有传输价值
- **硬约束下的最优传输**：当上行信道每请求只能传 50-200 bits 时，需要选择"云侧最需要知道的"而非"本地最不确定的"
- **对手机端的实际意义**：5G 上行带宽通常 5-20 Mbps，SAGE 确保在弱信号区域的端云推理仍可工作

## 关联

- [[edge-cloud-offloading]] — SAGE 是端云卸载的传输优化层
- [[micro-language-models-edge]] — μLM 的端云分割需要高效传输，SAGE 可优化
- [[comllm-mec-offloading]] — COMLLM 的边缘卸载框架中可集成 SAGE
- [[wisv-device-edge-speculative-decoding]] — WISV 也是设备-边缘推理优化
- [[on-device-inference-memory-pressure]] — 减少传输量间接降低端侧内存压力
