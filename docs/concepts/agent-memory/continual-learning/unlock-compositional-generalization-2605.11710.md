---
title: "Unlocking Compositional Generalization in Continual Few-Shot Learning"
arXiv: "2605.11710"
date: "2026-05-12"
tags: [agent-memory, continual-learning, few-shot-learning, compositional-generalization]
reviewer: auto
source: arXiv API
---

# Unlocking Compositional Generalization in Continual Few-Shot Learning

## 论文信息

| 字段 | 内容 |
|------|------|
| **作者** | Phu-Quy Nguyen-Lam, Phu-Hoa Pham, Dao Sy Duy Minh, Chi-Nguyen Tran, Huynh Trung Kiet, Long Tran-Thanh |
| **发表日期** | 2026-05-12 |
| **arXiv ID** | 2605.11710 |
| **类别** | cs.LG |
| **标签** | agent-memory, continual-learning, few-shot-learning, compositional-generalization |

## 摘要（翻译）

以对象为中心的表示为数样本学习（few-shot learning）承诺了一个关键特性：模型并非将场景作为单一单元处理，而是将其分解为可在不同概念间匹配和比较的独立对象级部件。然而在实践中，这一潜力很少实现。持续学习器要么将场景压缩为全局嵌入，要么用部件级匹配目标训练，使表示过度绑定于已见过的模式，导致无法泛化到真正全新的概念。本文识别了这一根本性的结构冲突，并开创性地提出一个严格解耦表示学习与组合推理的新范式。利用自监督视觉Transformer（ViT）固有的patch级语义几何，所提框架采用双阶段策略。训练时，slot表示完全针对整体类别身份优化，保持高度可泛化的对象级几何；推理时，保留的slots被动态组合以匹配新场景。这一范式提供双重结构优势：冻结骨干自然防止表示漂移，而轻量级整体优化保留了特征对新概念迁移的能力。大量实验验证了该方法，在标准持续学习基准上实现了最先进的未见概念泛化及最小遗忘。

## 核心贡献

1. **发现根本性结构冲突**：识别持续学习器在表示学习和组合推理之间的核心矛盾——整体优化导致部件级几何退化，而部件级匹配目标过度绑定已见模式

2. **严格解耦的新范式**：提出将表示学习与组合推理严格分离的框架，训练时优化整体类别身份，推理时动态组合slots

3. **双阶段策略**：
   - 训练阶段：slot表示完全针对整体类别身份优化
   - 推理阶段：动态组合保留的slots以匹配新场景

4. **双重结构优势**：冻结骨干自然防止表示漂移 + 轻量级整体优化保留新概念迁移能力

5. **最先进的泛化与最小遗忘**：在标准持续学习基准上实现SOTA未见概念泛化，同时保持最小遗忘

## 为什么重要

持续学习中的灾难性遗忘问题通常关注任务间的参数干扰，但本文从一个新的角度切入——**组合泛化的结构冲突**。当Agent需要不断学习新任务时，如何保证对全新场景的泛化能力？本文指出问题的根源在于表示学习和组合推理的目标不一致。解耦这两个阶段为构建更具适应性的持续学习系统提供了新思路，对需要处理不断变化环境的Agent记忆系统具有重要参考价值。

## 技术细节

### 核心方法

```
训练阶段：
  场景 → Self-supervised ViT → Patch几何特征
                              → Slot表示（整体类别优化）
                                 └─ 保持对象级几何可迁移性

推理阶段：
  新场景 → 冻结ViT提取Patch特征
          → 动态组合保留的Slots
          → 匹配新概念
```

### 关键设计

- **自监督ViT骨干**：利用patch级语义几何的固有能力
- **Slot表示机制**：通过整体类别身份优化，保持通用对象级几何
- **动态组合**：推理时自由组合slots以适应新场景

## 与移动端/端侧的相关性

1. **边缘设备持续适应**：移动端Agent需要在新任务到来时快速适应而不遗忘旧技能
2. **隐私敏感场景**：本地持续学习不需要上传数据到云端
3. **资源受限环境**：解耦表示学习与组合推理的设计适合轻量级部署

## 参考

- arXiv: https://arxiv.org/abs/2605.11710
