---
title: "Text Knows What, Tables Know When: Clinical Timeline Reconstruction via Retrieval-Augmented Multimodal Alignment"
arXiv: 2605.15168
date: 2026-05-14
tags: [agent-memory, memory-retrieval, multimodal, RAG, healthcare]
reviewer: auto
source: arXiv RSS/API
---

# 核心贡献

1. **多模态时间线对齐框架**：提出 retrieval-augmented multimodal alignment framework，将非结构化临床叙述（文本）与结构化 EHR 表格数据融合，提升临床事件时间线的绝对时间戳精度（AULTC指标）。
2. **图式多步重建流程**：将时间线重建建模为图式多步过程——首先从叙述中提取中心锚定事件构建初始时间骨架，再将非中心事件相对于该主干定位，最后用检索到的结构化 EHR 行作为外部时间证据进行校准。
3. **实证发现**：34.8% 的文本衍生事件完全不在表格记录中，说明单一模态会遗漏大量临床有意义的事件。

# 为什么重要

临床时间线重建是患者轨迹建模和风险预测的基础。传统方法依赖单一模态：文本语义丰富但时间精度差；表格数据时间精确但遗漏大量事件。本框架通过 RAG 机制弥合这一鸿掩，在 MIMIC-III/MIMIC-IV 数据集上显著提升时间戳准确性和事件匹配率。

# 与端侧/移动端的相关性

医疗是边缘部署的重要场景——ICU 监护、可穿戴健康监测均需要本地处理患者数据。本框架的 retrieval-augmented 范式可在边缘设备上实现快速临床事件检索，同时通过 EHR 外部记忆库提升推理准确性。

# 标签

`memory-retrieval` `multimodal-memory` `healthcare` `RAG` `clinical-agents`

# 核心方法

## 框架结构

1. **锚定事件提取**：从非结构化临床叙述中使用指令微调 LLM 提取中心事件，构建初始时间骨架
2. **非中心事件放置**：将边缘临床事件相对于锚定事件进行时间定位
3. **外部时间证据检索**：从结构化 EHR 表格中检索时间证据，对重建时间线进行校准
4. **多模态对齐**：通过跨模态对齐确保文本语义与表格时间戳一致

## 实验结果

在 i2m4 benchmark（MIMIC-III 和 MIMIC-IV）上评估：
- 绝对时间戳准确性（AULTC）显著提升
- 时间一致性在几乎所有评估模型上均有改善
- 事件匹配率未受影响

# 参考文献

（参考文献待从原文补充）
