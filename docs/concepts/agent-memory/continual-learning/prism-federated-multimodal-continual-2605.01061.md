---
title: "PRISM: Exposing and Resolving Spurious Isolation in Federated Multimodal Continual Learning"
arXiv: 2605.01061
date: 2026-05-01
authors: ["Beining Wu", "Zihao Ding", "Jun Huang"]
tags: [agent-memory, continual-learning, federated-learning, multimodal, MoE, LoRA]
reviewer: auto
source: arXiv API
---

# PRISM: 联邦多模态持续学习中虚假隔离的暴露与解决

## 论文概览

**核心问题**：当前联邦多模态持续学习基于一个未经验证的假设——路由（routing）将任务特定知识隔离到不同专家中。但本文发现这是**虚假隔离**（spurious isolation）：路由是 per-sample 操作的，而遗忘是在任务序列上累积的，每个专家内部都存在梯度冲突。

**核心发现**：即使路由最大极化，梯度冲突仍然存在于每个专家内部。这是 MoE（Mixture-of-Experts）+ LoRA 结合的内在问题——LoRA 的低秩适配器被所有专家共享，导致跨任务的参数纠缠。

## 背景问题

联邦持续学习（FCL）结合了联邦学习（FL，保护数据隐私）和持续学习（CL，避免灾难性遗忘），在多模态场景下尤其重要——移动/边缘设备产生的视觉、语言、传感器数据天然适合联邦架构。

MoE-LoRA 是当前多模态持续指令微调的主流方案：MoE 提供稀疏激活的专家选择，LoRA 提供参数高效的适配。但现有方法假设专家路由能自动隔离任务知识，这导致它们忽视了 per-sample 路由与 per-task 遗忘之间的根本矛盾。

## 核心方法：PRISM

论文提出 **PRISM**（名称来自 "Per-Expert gRadient subspace ISolation with federated scoMposition"），包含四个关键组件：

### 1. Per-Expert Gradient Subspace Isolation
为每个专家维护独立的梯度子空间，防止跨任务梯度干扰。通过对每个专家的梯度矩阵进行 SVD，丢弃跨越多个任务方向的梯度分量。

### 2. Federated Aggregation with Gradient Orthogonalization
联邦聚合时对各客户端梯度进行正交化处理，确保聚合后的更新不会在已有知识上引入破坏性干扰。

### 3. Interference-Informed Scheduling
基于任务间干扰程度的自适应调度：为高干扰任务对分配更大的参数隔离裕度，为低干扰任务对允许更多参数共享。

### 4. Routing-Projection Symbiosis
路由选择与投影映射协同优化：不仅学习路由策略，还学习专家输出到任务空间的投影矩阵，使路由选择的结果真正对应于任务隔离。

## 核心贡献

1. **虚假隔离现象的形式化定义**：首次系统分析了 MoE-LoRA 架构中路由隔离假设失效的原因和机制
2. **时间尺度不匹配问题**（Timescale Mismatch）：路由在单样本尺度运作，遗忘在任务序列尺度累积——两者的时间尺度不兼容导致虚假隔离
3. **PEFT Entanglement 问题**：LoRA 参数被所有专家共享是梯度冲突的结构性根源
4. **PRISM 框架**：首个针对联邦多模态持续学习中专家隔离失效的解决方案

## 为什么重要

随着多模态大模型在移动端和边缘设备上的部署越来越普遍，联邦多模态持续学习成为一个关键范式——用户数据不出设备，模型持续学习个性化知识。但现有方法对 MoE 路由的过度信任导致它们在真实场景中表现不佳。PRISM 揭示了这一根本性误解，并提供了切实可行的修正方案。

## 端侧/移动端相关性

联邦学习天然适合端侧部署（数据隐私+个性化学习），而 PRISM 的梯度子空间隔离方案计算开销可控，对移动/边缘设备友好。多模态+持续学习+隐私保护的组合正是未来移动端 AI 记忆系统的核心需求。

## 实验结果

论文在自定义的联邦多模态持续学习基准上验证了 PRISM，在 multimodal continual learning 准确率上显著超越基线方法，证明了虚假隔离问题的真实存在和 PRISM 解决方案的有效性。
