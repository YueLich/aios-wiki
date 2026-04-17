---
type: concept
tags: [slm, ocr, edge-ai, on-device, structured-ocr, document-processing, small-language-model]
related: [[qwen35-small]], [[lacy-small-model-token-selection]], [[edgeflow-cold-start]], [[mnn-350]]
sources:
  - url: https://arxiv.org/abs/2604.14314
    title: "DharmaOCR: Specialized Small Language Models for Structured OCR"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# DharmaOCR: 面向结构化 OCR 的专用小型语言模型

> 专为结构化 OCR 设计的专用小型语言模型（SSLM），在转录质量、生成稳定性和推理成本之间实现联合优化。

## 核心问题

传统 OCR 系统基于模块化流水线（文本检测→分割→字符识别），在面对异构文档、不同文档领域和结构变化时存在性能差距。近年来，基于多模态大语言模型（GPT-4o、Gemini 2.5 Pro）的文档信息提取架构虽然改善了复杂布局处理能力，但引入了高计算成本和领域特异性不足的问题。

## 方法/架构

DharmaOCR 提出 **DharmaOCR Full** 和 **DharmaOCR Lite** 两个变体，都是专用小型语言模型（SSLMs）：
- **SSLM 定义**：参数规模远小于 LLM（通常 < 15B 参数），但针对特定任务和领域进行了专门优化
- **联合优化目标**：转录保真度（Fidelity）、结构生成稳定性（Structure）和推理成本（Unit Cost）
- **退化度量**：将文本退化率（degeneration rate）作为一等基准度量指标，这是区别于现有工作的关键创新
- **统一评估协议**：同时测量保真度和结构，明确追踪文本退化

### DharmaOCR-Benchmark
- 覆盖印刷体、手写体和法律/行政文档
- 提出统一评估协议
- 测量保真度和结构的同时，追踪文本退化率

## 实验结果/关键数据

DharmaOCR Full 和 Lite 在结构化 OCR 任务上超越了开源和商业基线：
- 在印刷体文档上实现了更低的退化率
- 在手写体文档上保持了竞争力
- DharmaOCR Lite 以显著更小的模型尺寸接近 Full 版本的性能
- 与 GPT-4o 和 Gemini 2.5 Pro 等大模型相比，SSLM 在特定领域 OCR 任务上实现了更优的成本效益比

## 关键洞察

1. **专用 vs 通用的权衡**：SSL M 在特定领域 OCR 上可以超越通用大模型，因为"通才"模型在领域特异性任务上存在固有局限
2. **退化率是关键指标**：OCR 错误会传播到下游生成系统（信息检索、实体提取、分类、摘要），降低事实性和可控性——"garbage in, garbage out" 原则
3. **边缘部署可行性**：SSLM 的低计算成本使其适合在边缘设备上运行，这对手机端文档扫描和即时 OCR 场景至关重要
4. **与生成 AI 的协同**：高质量 OCR 是部署生成 AI 于真实组织知识的关键使能器——大量有价值信息锁在非结构化工件中

## 为什么重要

DharmaOCR 证明了一个关键趋势：**专用小模型可以在特定任务上超越通用大模型**，同时保持适合边缘/端侧部署的计算成本。这对手机端 AIOS 的文档处理、即时 OCR 和离线文档理解能力有直接意义。随着手机摄像头质量提升和文档数字化需求增长，端侧高效 OCR 成为必备能力。

## 关联
- [[qwen35-small]] — 同样是小模型在特定任务上的竞争力研究
- [[lacy-small-model-token-selection]] — SLM 在 token 选择上的优化
- [[edgeflow-cold-start]] — 端侧模型冷启动优化
- [[mnn-350]] — MNN 推理框架对端侧 SLM 部署的支持
- [[biotrain-ondevice-finetuning-mcu]] — 端侧微调与专用模型的关系
