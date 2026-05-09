---
title: "Temporal Memory for Resource-Constrained Agents: Continual Learning via Stochastic Compress-Add-Smooth"
arXiv: 2604.00067
date: 2026-03-31
authors: ["Michael Chertkov"]
tags: [agent-memory, continual-learning, memory-compression, stochastic-process, resource-constrained]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.00067
- **发表日期**: 2026-03-31
- **作者**: Michael Chertkov
- **方向**: 持续学习（资源受限 Agent 的时序记忆）

## 摘要

**背景**：顺序操作的 Agent 必须在固定记忆预算下整合新经验而不遗忘旧经验。传统方法将记忆视为参数向量，通过梯度下降更新，但这需要大量存储和计算。

**方法**：本文提出将记忆建模为随机过程——Replay 区间 $[0,1]$ 上的 Bridge Diffusion，其终端边缘编码当前时刻，中间边缘编码过去。新经验通过三步"压缩-添加-平滑"（CAS）递归整合。框架在边际概率密度通过高斯混合模型建模的场景下进行测试，类内复杂度由分段线性协议节点数 $L$ 控制。

**关键发现**：遗忘来自有损时序压缩——在固定段预算下将细粒度协议重新近似为粗粒度协议。遗忘半衰期 $a_{1/2} \approx c\,L$ 与 $L$ 成线性关系，常数 $c$ 具有类似 Shannon 信道容量的信息论解释。整个递归每次迭代仅需 $O(LKd^2)$ FLOPs，无需反向传播、存储数据或神经网络，适合轻量级控制器硬件。

## 核心贡献

1. **随机过程记忆框架**：将 Agent 记忆从参数向量转变为 Bridge Diffusion 随机过程，提供时序连贯的"电影式"回放
2. **CAS 递归机制**：Compress-Add-Smooth 三步递归，无需反向传播，适合资源受限硬件
3. **解析遗忘理论**：遗忘半衰期与协议段数线性相关，提供可数学证明的持续学习框架
4. **无神经网络设计**：纯解析方法（Ising 模型类比），适合无法运行深度学习的嵌入式/控制器场景

## 为什么重要

这是少见的**纯解析持续学习理论**工作，提供了：

- **可证明的遗忘界**：遗忘半衰期的线性标度性质是第一个具有严格数学证明的结果
- **资源受限场景**：无需 GPU/TPU，适合 IoT 传感器、嵌入式控制器等端侧设备
- **桥接理论与实践**：将随机过程理论（Bridge Diffusion）与 Agent 记忆问题连接

## 与端侧/移动端的相关性

本文与端侧记忆系统高度相关：

- **嵌入式 Agent**：无需反向传播，适合微控制器和轻量级边缘设备
- **固定记忆预算**：直接在数学上建模固定存储约束，而非依赖经验性的压缩比
- **能效优化**：$O(LKd^2)$ 复杂度远低于梯度下降，适合电池供电设备

## 参考文献

- arXiv: 2604.00067 | https://arxiv.org/abs/2604.00067
