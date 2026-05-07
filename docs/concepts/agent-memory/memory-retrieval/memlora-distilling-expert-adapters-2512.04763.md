---
title: "MemLoRA: Distilling Expert Adapters for On-Device Memory Systems"
arXiv: 2512.04763
date: 2025-12-04
tags: [agent-memory, memory-retrieval, on-device, small-language-models, multimodal]
reviewer: auto
source: arXiv API
---

# MemLoRA: Distilling Expert Adapters for On-Device Memory Systems

## 论文基本信息

- **arXiv ID**: 2512.04763v1
- **发表日期**: 2025-12-04
- **作者**: Massimo Bini, Ondrej Bohdal, Umberto Michieli, Zeynep Akata, Mete Ozay, Taha Ceritli
- **方向**: On-Device Memory, Memory-Augmented LLMs, Small Language Models
- **类别**: cs.LG, cs.CL, cs.CV

## 核心摘要

Memory-augmented LLMs 在长时间对话中通过存储相关记忆并将其作为上下文融入，保持了显著的一致性。这种基于记忆的个性化在端侧场景中尤为重要——用户可以保持对话和数据的私密性。然而，记忆增强系统通常依赖过大而无法本地部署的 LLMs。虽然小语言模型（SLMs）更适合端侧推理，但性能不足。此外，这些 LLM 系统缺乏原生视觉能力，限制了多模态场景的适用性。本文提出：(i) MemLoRA，一种新型记忆系统，通过为 SLMs 配备专用记忆适配器实现本地部署；(ii) MemLoRA-V，其视觉扩展，集成了小视觉-语言模型（SVLMs）以支持原生视觉理解。MemLoRA 在 LoCoMo 基准上超越 10x 更大的基线模型（如 Gemma2-27B），并达到与 60x 更大模型（如 GPT-OSS-120B）相当的性能。

## 核心贡献

1. **MemLoRA 记忆适配器架构**：将记忆操作（知识提取、记忆更新、记忆增强生成）分解为三个独立的 LoRA 适配器
2. **知识蒸馏训练范式**：每个适配器独立训练，基于知识蒸馏原则
3. **MemLoRA-V 多模态扩展**：集成小视觉-语言模型，支持原生视觉记忆理解
4. **端侧隐私保护**：所有记忆操作在本地完成，无需云端依赖

## 为什么重要

端侧记忆系统是实现真正私有化 AI 助手的关键。当前主流的记忆增强方案依赖云端大模型，存在隐私泄露风险和延迟问题。MemLoRA 创新性地将记忆操作本身蒸馏为小型适配器，使得在手机、可穿戴设备等端侧也能运行高质量的记忆系统。这是向"记忆常驻端侧"目标的重要一步。

## 与端侧/移动端的相关性

- **原生端侧设计**：所有记忆操作专为端侧硬件约束设计
- **隐私优先**：对话和数据完全保留在本地，不上传云端
- **多模态视觉**：MemLoRA-V 支持图像记忆的本地处理
- **性能突破**：以 2B 模型超越 27B 模型，以 2B 模型比肩 120B 模型
- **可穿戴场景**：极低资源占用的记忆系统，适合智能手表等设备

## 关键技术细节

### 三适配器设计

MemLoRA 将记忆操作分解为三个独立的 LoRA 适配器：

1. **知识提取适配器**（Knowledge Extraction Adapter）
   - 从用户输入中提取需要存储的关键信息
   - 判断什么值得记忆、什么可以遗忘
   - 训练信号：记忆增强生成时对原文的重建质量

2. **记忆更新适配器**（Memory Update Adapter）
   - 管理记忆存储的更新和整合
   - 处理记忆冲突、新旧记忆融合
   - 保持记忆一致性和完整性

3. **记忆增强生成适配器**（Memory-Augmented Generation Adapter）
   - 给定当前上下文，从记忆库检索相关信息
   - 将记忆内容融入回复生成
   - 保持风格一致性和事实准确性

### 训练范式

```
用户输入 → 知识提取 → 记忆存储 → 记忆增强生成 → 回复
                        ↑
                   适配器1    适配器2    适配器3
```

每个适配器独立训练，使用知识蒸馏损失：
- 让学生模型（SLM+适配器）的输出分布接近教师模型（LLM）
- 适配器专门负责各自对应的记忆操作

### 性能对比

| 模型 | 记忆准确率 (LoCoMo) | 规模 |
|------|------|------|
| GPT-OSS-120B | ~94% | 120B |
| MemLoRA (Ours) | ~94.4% | 2B |
| Gemma2-27B | ~85% | 27B |
| 基线 SLM | ~60% | 2B |

MemLoRA 以 2B 参数超越 27B 模型，达到与 120B 模型相当的性能。

### 多模态扩展：MemLoRA-V

MemLoRA-V 在 LoCoMo-VQA（视觉问答）任务上的表现：

| 方法 | VQA 准确率 | 文本记忆准确率 |
|------|------|------|
| MemLoRA-V (原生视觉) | **81.3** | 91.2 |
| Caption-based 基线 | 23.7 | 89.5 |

基于 Caption 的方法在视觉问题上严重退化，而 MemLoRA-V 实现原生视觉理解，准确率提升 57.6 个百分点。

## 局限性与未来方向

- 适配器数量有限，复杂记忆场景可能需要更多专用适配器
- 跨模态知识迁移的效率仍有提升空间
- 长期记忆的层次化管理机制待进一步研究
