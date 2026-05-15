---
title: "Forgetting That Sticks: Quantization-Permanent Unlearning via Circuit Attribution"
arXiv: 2605.15138
date: 2026-05-14
tags: [agent-memory, memory-privacy, unlearning, quantization]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文揭示了一个关键问题：标准机器遗忘（unlearning）评估在全精度下立即测量行为抑制，但实际部署的模型都经过量化（4-bit）。研究表明 4-bit 量化可以逆转机器遗忘——这是稀疏性-永久性权衡的系统性双重失效：要么遗忘效果在量化后消失，要么量化后存活的模型几乎没有改变。论文提出 MANSU（Mechanistic-Aligned Null-Space Unlearning），通过因果电路归因隔离最小遗忘子图，结合电路限制的零空间投影和对数量级下界，首次实现量化后仍可保持遗忘效果。引入 CAD（Circuit Attribution Divergence）作为结构性擦除与行为抑制的验证指标。

## 核心贡献

1. **揭示量化与遗忘的双重失效**：梯度方法在量化后失去遗忘效果（per-parameter 更新比 NF4 量化 bin 宽度小 47-828 倍）；而能在量化中存活的方法几乎没有改变模型。

2. **稀疏性-永久性权衡的形式化**：证明跨所有基线，参数更新分散在数十亿参数上，无法清除量化 bin 边界。

3. **MANSU 方法**：结合因果电路归因（隔离最小 forget-set 子图）、电路限制零空间投影（带对角 Fisher retain bound）、per-parameter 幅度下界（保证量化 survivability）。

4. **CAD 指标**：区分结构性擦除与行为抑制，是现有指标无法做到的。

5. **四属性联合满足**：在多个模型家族和基准上，MANSU 首次同时满足有意义遗忘、保留保持、非正量化差距和结构性擦除四个属性。

## 为什么重要

当用户要求"删除某个训练数据的影响"时，实际部署的量化模型可能完全忽略这一请求。这对需要处理敏感数据的端侧 AI 系统（手机、 wearable 设备）有直接影响——设备上的模型可能保留不应该存在的记忆，且无法通过标准 unlearning 技术修复。MANSU 为端侧隐私保护提供了可行的技术路径。

## 与移动端/端侧的相关性

移动设备和可穿戴设备上的 AI 模型通常使用 4-bit 量化以适应有限的计算资源。本文证明这些设备上的机器遗忘请求可能完全无效——敏感数据即使被请求遗忘，在量化后仍可能影响模型输出。MANSU 的量化感知遗忘机制对保护端侧用户隐私有直接意义。

## 参考文献

（参考文献待从原文补充）
