---
title: Retrieval-Augmented Memory for Online Learning
arXiv: 2512.02333
date: 2025-12-02
tags: [agent-memory, memory-retrieval, continual-learning, RAG]
reviewer: auto
source: arXiv API
---

# Retrieval-Augmented Memory for Online Learning (RAM-OL)

## 摘要

检索增强模型将参数化预测器与非参数化记忆结合，但其在概念漂移 streaming 监督学习中的使用尚未被充分研究。本文研究非平稳环境中的在线分类问题，提出 Retrieval-Augmented Memory for Online Learning (RAM-OL)，即随机梯度下降的简单扩展，维护少量过去示例的缓冲区。在每个时间步，RAM-OL 检索当前输入在隐藏表征空间中最近的邻居，并用其增强模型预测。

## 核心贡献

1. **RAM-OL 方法**：将 RAG 思想引入在线持续学习
2. **隐藏空间近邻检索**：在特征空间而非输入空间检索相关记忆
3. **概念漂移适应**：通过记忆中的历史模式检测和适应分布变化
4. **计算高效**：仅维护小型缓冲区，无需存储全部历史
5. **即插即用**：可与任意在线学习算法结合

## 技术方法

### 核心机制
- **记忆缓冲区**：维护少量有代表性的历史样本
- **近邻检索**：在每个时间步找到与当前输入最相似的记忆
- **记忆增强预测**：将检索到的近邻样本加入梯度计算
- **自适应缓冲区管理**：根据样本重要性动态替换记忆

### 与传统 RAG 的区别
传统 RAG 从外部文档检索，RAM-OL 从模型自身的"经验记忆"检索——记忆本身就是模型过去学习过程的产物。

## 为什么重要

这篇论文将"记忆"从静态文档存储扩展到了动态学习过程的产物。对于构建能"从经验中持续学习"的 Agent 系统有重要启发：Agent 不仅要从外部知识库检索，还要能从自身过去的交互经验中快速学习。

## 与移动端/端侧相关性

1. **边缘 AI 持续学习**：在资源受限设备上持续适应新任务
2. **个性化推荐**：基于用户历史行为的在线学习
3. **异常检测**：从正常模式记忆中检测偏离
4. **低功耗学习**：无需云端即可持续学习新模式

## 参考文献

- Wenzhang Du. "Retrieval-Augmented Memory for Online Learning." arXiv:2512.02333, 2025.
