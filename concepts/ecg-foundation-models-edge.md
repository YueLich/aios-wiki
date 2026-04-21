---
type: concept
tags: [edge-ai, medical-ai, foundation-model, ecg, wearable, cardiovascular, llm]
related: [[ondevice-streaming-asr]], [[wearable-large-sensor-models]]
sources:
  - url: https://arxiv.org/abs/2604.02501
    title: "ECG Foundation Models and Medical LLMs for Agentic Cardiovascular Intelligence at the Edge"
    date: 2026-04-02
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# 边缘端 ECG 基础模型与医疗 LLM：心血管 AI Agent 综述

> 综述 ECG 基础模型和医疗 LLM 在边缘心血管智能中的应用，提出从任务特定管线到通用架构的范式转变

## 核心问题

心血管疾病（CVD）是全球首要死因。心电图（ECG）是 CVD 筛查、诊断和监测的核心工具。传统方法：
- **人工判读**：依赖专家，耗时且主观
- **任务特定深度学习**：每个任务（心律失常、缺血、风险预测）需要单独训练，泛化能力差
- **部署到边缘**：穿戴设备上需要实时处理，算力和功耗受限

## 方法：基础模型 + 医疗 LLM 融合

### ECG 基础模型（Foundation Models）
- 在大规模无标签 ECG 波形数据上预训练
- 学习层次化表示，可迁移到心律失常检测、缺血识别、风险预测等任务
- 接近专家水平的判别性能

### 医疗 LLM 集成
- Med-PaLM、Med-Gemma、BioGPT 等医疗 LLM 提供临床知识推理能力
- 挑战：这些 LLM 主要在文本语料上训练，不直接理解生理信号
- **关键创新方向**：将 ECG 基础模型的信号表示与 LLM 的推理能力融合

### 边缘部署架构
```
可穿戴 ECG 传感器
  → ECG 基础模型（信号编码）
  → 医疗 LLM（临床推理）
  → 实时风险评估 & 告警
```

## 实验结果

综述汇总了多个基准的性能数据：
- ECG 基础模型在心律失常检测上达到接近专家水平
- 穿戴设备上的边缘推理延迟在可接受范围内
- 但跨异质采集设置的鲁棒性仍是挑战

## 关键洞察

1. **从任务特定到通用**：基础模型范式使 ECG AI 从"每个任务一个模型"变为"一个模型多个任务"
2. **信号 + 语言 = 临床智能**：纯文本 LLM 不理解 ECG 波形，需要多模态融合
3. **边缘部署的三重约束**：准确性、延迟、功耗在穿戴设备上比手机更严格
4. **纵向数据整合**：基础模型可整合患者的长期 ECG 记录，而非仅看单次采集

## 为什么重要

穿戴设备（智能手表、心电贴片）的普及使连续 ECG 监测成为可能。基础模型 + LLM 的融合方案意味着：
- 穿戴设备可实时检测心律失常并给出临床建议
- 不需要云端连接即可完成初步诊断
- 对偏远地区和发展中国家的医疗可及性有重大意义

## 关联
- [[ondevice-streaming-asr]] — 端侧推理优化技术同样适用于 ECG 模型部署
- [[wearable-large-sensor-models]] — 可穿戴 AI 的传感器模型与 ECG 基础模型有共通架构
