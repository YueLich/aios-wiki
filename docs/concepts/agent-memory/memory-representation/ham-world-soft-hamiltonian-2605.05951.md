---
title: "HaM-World: Soft-Hamiltonian World Models with Selective Memory for Planning"
arXiv: 2605.05951
date: 2026-05-07
tags: [agent-memory, memory-representation, world-models, planning, selective-memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **作者**: Haoyun Tang, Haodong Cui, Keyao Xu, Kun Wang, Zhandong Mei
- **机构**: 上海交通大学 (Shanghai Jiao Tong University)
- **发表日期**: 2026-05-07
- **开源代码**: https://github.com/HaoyunT/HaM_World

## 一句话总结

HaM-World 通过将潜状态分解为守恒的哈密顿子空间 (q,p) 和耗散的上下文子空间 c，并使用选择性状态空间记忆 (Mamba) 提供历史条件输入，解决了世界模型在长视野规划和分布外场景中的不稳定问题。

## 摘要（翻译）

世界模型通过学习的潜动态实现基于模型的规划，但随着规划视野增长或动态分布偏移，想象的 rollout 会变得不稳定。本文认为这种不稳定性源于 planner 面对的潜状态中缺少两种结构：**近似马尔可夫完整性的历史条件记忆**，以及**分离配置、动量和任务语义的几何组织**。

本文提出 **HaM-World (HMW)**，一种结构化世界模型，将潜状态分解为：
- **正则子空间 (q,p)**：通过能量导出的哈密顿向量场演化，包含可学习的残差/控制动态
- **上下文子空间 c**：捕获语义、耗散和非保守因素

同时使用 **Mamba 选择性状态空间记忆** 作为历史条件输入。在 4 个 DeepMind Control Suite 任务上，HaM-World 达到最高平均 AUC (117.9, +9.5%)，将长视野 rollout 误差降低到强基线的 45%，在 {3,5,7} MSE 单元中赢得 11/12 k。在 12 种分布外扰动（动态偏移、动作延迟、观察遮挡）下，HaM-World 在每种条件下均达到最高 return，在 Finger Spin 上平均 OOD return 提升 10.2%，Reacher Easy 上提升 13.6%。

## 核心贡献

### 1. 潜状态几何分解
将 planner 可见的潜状态显式分解为：
- **正则分量 (q,p)**：满足哈密顿力学，提供能量守恒和可逆性
- **上下文分量 c**：耗散的、语义编码的、非保守力

这种分解使得规划器可以共享同一个潜状态用于动态预测、奖励/价值估计、想象 rollout 和 CEM 动作搜索。

### 2. 选择性记忆接口
使用 **Mamba 选择性状态空间模型 (SSM)** 作为历史条件记忆：
- 不同于固定窗口记忆或全注意力机制
- 选择性决定保留/遗忘哪些历史信息
- 为 planner 提供近似马尔可夫完备性（减少对完整历史的依赖）

### 3. 机制诊断
通过诊断验证了设计意图：
- 有界无动作哈密顿能量漂移
- 策略 rollout 下结构化能量变化
- 一致性控制诱导能量转移

## 关键方法细节

### Soft-Hamiltonian 动态
(q,p) 子空间通过以下方式演化：

$$\dot{q} = \nabla_p H(q,p), \quad \dot{p} = -\nabla_q H(q,p) + \text{残差动态}$$

其中哈密顿量 H(q,p) 学习能量函数，残差动态捕获非保守力（摩擦、耗散）。

### 选择性记忆机制
Mamba SSM 作为记忆模块：
- 输入：历史观测序列
- 输出：上下文向量 c 的历史条件
- 选择性：输入门控决定历史信息保留程度

### 统一规划接口
同一潜状态 (q,p,c) 用于：
1. 动态预测（向前 rollout）
2. 奖励/价值估计
3. CEM（交叉熵方法）动作搜索

## 为什么重要

### 解决世界模型的核心瓶颈
世界模型的"想象不稳定"问题是基于模型 RL 的主要障碍：
- 误差随 rollout 步数累积
- 分布外状态导致荒唐的预测

HaM-World 通过几何结构（能量守恒提供内在稳定性）和选择性记忆（防止历史污染）双管齐下解决。

### 对 Agent Memory 的启示
本文展示了**任务相关记忆的选择性**对长视野规划至关重要：
- 不是所有历史都同等重要
- 记忆应该支持可逆的、守恒的动态建模
- Mamba SSM 的选择性机制可作为记忆压缩的参考

## 与移动端/端侧的相关性

### 高计算效率
- Mamba SSM 计算效率高于全注意力
- 单个潜状态服务多个规划任务，减少冗余计算
- 适合边缘设备上的实时规划

### 资源受限场景
能量守恒的动态提供内在稳定性，减少了对精确模型的需求——这对边缘部署有利。

### 未来端侧应用
结合选择性记忆的世界模型可应用于：
- 机器人实时控制（需要低延迟长视野规划）
- 自动驾驶的认知预测
- AR/VR 环境建模

## 实验结果

### DeepMind Control Suite
| 任务 | HaM-World AUC | 基线最优 AUC | 提升 |
|------|--------------|-------------|------|
| 平均 | 117.9 | 107.5 | +9.5% |
| Long-horizon rollout error | 45% of baseline | - | - |

### 分布外鲁棒性（12 种扰动）
- 动态偏移、动作延迟、观察遮挡
- 在**所有**条件下达到最高 return
- Finger Spin OOD return +10.2%
- Reacher Easy OOD return +13.6%

## 参考文献

- 论文主页: https://arxiv.org/abs/2605.05951
- 开源代码: https://github.com/HaoyunT/HaM_World
- Authors: Haoyun Tang, Haodong Cui, Keyao Xu, Kun Wang, Zhandong Mei (Shanghai Jiao Tong University)
