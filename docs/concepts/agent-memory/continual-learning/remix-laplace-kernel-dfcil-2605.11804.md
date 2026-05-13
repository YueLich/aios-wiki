---
title: "Stop Marginalizing My Dreams: Model Inversion via Laplace Kernel for Continual Learning"
arXiv: "2605.11804"
date: "2026-05-12"
tags: [agent-memory, continual-learning, data-free-continual-learning, model-inversion, laplace-kernel]
reviewer: auto
source: arXiv API
---

# Stop Marginalizing My Dreams: Model Inversion via Laplace Kernel for Continual Learning

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Patryk Krukowski, Jacek Tabor, Przemysław Spurek, Marek Śmieja, Łukasz Struski |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.11804 |
| **类别** | cs.LG |
| **标签** | agent-memory, continual-learning, data-free-continual-learning, model-inversion, laplace-kernel |

## 摘要（翻译）

数据-free 持续学习（DFCIL）依赖模型反转来合成伪样本并缓解灾难性遗忘。但现有反转方法受限于一个根本性假设：使用对角协方差建模特征分布，实际上忽略了定义所学表示几何结构的特征相关性。因此，合成的样本往往缺乏保真度，知识保留受限。本文证明建模特征依赖性是有效 DFCIL 的关键要素。提出 REMIX，利用拉普拉斯核参数化实现结构化协方差建模，使全协方差建模可在不产生密集矩阵求逆和行列式计算的计算成本下扩展。

## 核心贡献

1. **REMIX 框架**：首个在 DFCIL 中实现全协方差建模的方法，通过拉普拉斯核参数化避免密集矩阵运算
2. **特征依赖性建模**：突破了对角协方差的简化假设，捕获特征间的相关性以生成更保真的伪样本
3. **可扩展性**：通过核参数化实现计算效率，使全协方差建模在大型模型中可行
4. **知识保留提升**：实验表明相比对角协方差方法，REMIX 能更有效地保留先前学习的知识

## 为什么重要

REMIX 的核心洞察是：**先前学习的知识不仅存在于参数中，还存在于参数间的相关性（协方差结构）中**。对于 Agent 记忆系统，这意味着遗忘不仅仅是参数值的丢失，更是参数关联结构的丢失。保留记忆的完整性需要同时保留权重和权重间的相关性。

## 与移动端/端侧的相关性

- 拉普拉斯核参数化方法相比密集协方差计算更适合端侧资源约束
- 无需存储历史数据的伪样本生成方式降低了端侧记忆存储开销
- 可与差分隐私技术结合，在端侧实现隐私保护的持续学习

## 参考文献

- Krukowski, P., Tabor, J., Spurek, P., Śmieja, M., & Struski, Ł. (2026). Stop Marginalizing My Dreams: Model Inversion via Laplace Kernel for Continual Learning. arXiv:2605.11804.
