---
type: concept
tags: [slm, llm, 端侧推理, 模型压缩, 知识蒸馏, 量化, 对比分析]
related: [[gemma4-ondevice]], [[qwen35-small]], [[lacy-small-model-token-selection]], [[septq-post-training-quantization]], [[biotrain-ondevice-finetuning-mcu]]
sources:
  - url: https://hn.algolia.com/api/v1/items/47000145
    title: "Small Language Models (SLMs) vs. Large Language Models (LLMs)"
    date: 2026-04-16
    reliability: medium
created: 2026-04-16
updated: 2026-04-16
---

# 小语言模型 vs 大语言模型：端侧推理的模型选型指南

> SLM 与 LLM 的系统性对比——覆盖设计、训练、部署和应用维度。

## 核心问题

大语言模型（LLM，数十亿到数千亿参数）在零样本推理、指令遵循和多轮对话上持续突破，但需要大型 GPU/TPU、可靠云连接和高推理成本——这些约束严重阻碍了低延迟、隐私保护和离线应用场景（移动端、机器人、IoT）。

小语言模型（SLM，通常 < 7B 参数）经过任务优化，可以在设备端或受限服务器上运行，缩小了与 LLM 的能力差距，同时开启了新的应用场景。

## 维度对比

| 维度 | SLM (< 7B) | LLM (> 70B) |
|------|-----------|-------------|
| **参数量** | 0.1B ~ 7B | 70B ~ 1.8T |
| **推理延迟** | 毫秒~秒级（端侧） | 秒~十秒级（云端） |
| **内存需求** | 1~14GB（可量化到 <4GB） | 140GB+（多GPU） |
| **部署环境** | 手机、边缘设备、IoT | 数据中心 |
| **隐私性** | ✅ 数据不出设备 | ❌ 数据上传云端 |
| **离线能力** | ✅ | ❌ |
| **零样本泛化** | 有限 | 强 |
| **多步推理** | 弱 | 强 |
| **训练成本** | 低~中 | 极高 |

## 核心压缩技术

### 1. 知识蒸馏（Knowledge Distillation）
- Teacher-Student 架构：用大模型指导小模型训练
- 代表：DistilBERT、TinyLlama（1.1B，从 Llama 2 蒸馏）
- 典型压缩比：教师模型 1/3 参数保留 97% 性能

### 2. 量化（Quantization）
- FP32 → INT8/INT4：模型大小缩减 4-8 倍
- 后训练量化（PTQ）：无需重新训练
- 量化感知训练（QAT）：训练时模拟量化，精度更高
- 代表：GGUF/GPTQ/AWQ 格式

### 3. 参数高效微调（PEFT）
- LoRA/QLoRA：仅训练 0.1-1% 参数
- 适配器（Adapters）：在冻结模型上添加轻量模块
- Prefix Tuning：优化虚拟 token 前缀

### 4. 剪枝（Pruning）
- 结构化剪枝：移除整个注意力头/层
- 非结构化剪枝：移除单个权重（需要稀疏硬件支持）
- 移动端挑战：非结构化剪枝在 ARM CPU 上收益有限

## 代表性 SLM

| 模型 | 参数量 | 特色 |
|------|--------|------|
| Gemma 2 | 2B/7B | Google 出品，端侧优化 |
| Qwen 3.5 | 0.6B~7B | 阿里通义千问小模型系列 |
| MiniCPM | 0.5B~8B | 端侧多模态领先 |
| Phi-3 | 3.8B | 微软，小模型推理突破 |
| TinyLlama | 1.1B | 超轻量，IoT 场景 |
| Apple Intelligence | 3B | Apple 端侧主力模型 |

## 关键洞察

1. **SLM 不是 LLM 的降级版**：通过蒸馏+量化+任务微调的组合拳，SLM 在特定任务上可以达到甚至超过通用 LLM。差距主要在需要深层推理和广泛知识的任务上。

2. **端侧推理的瓶颈正在被打破**：NPU、移动端 GPU（如 Apple Neural Engine、高通 Hexagon）的进步使得 7B 模型在手机上以可接受的延迟运行。

3. **SLM + LLM 混合架构**：越来越多的系统采用"SLM 处理简单任务 + LLM 处理复杂任务"的分层策略（如 Apple Intelligence 的端云协同）。

4. **隐私驱动 SLM 需求**：欧盟 AI 法案、各国数据主权法规推动了对端侧推理的需求，SLM 是唯一可行的离线隐私保护方案。

## 为什么重要

SLM vs LLM 的选型是移动 AIOS 架构设计的核心决策。选择 SLM 意味着更低延迟、更好隐私和离线能力，但需要在功能上做出妥协。理解两者的权衡对于设计端侧 Agent 系统至关重要。

## 关联
- [[gemma4-ondevice]] — Gemma 4 端侧部署
- [[qwen35-small]] — Qwen 3.5 小模型系列
- [[lacy-small-model-token-selection]] — SLM 的 token 选择策略
- [[septq-post-training-quantization]] — 后训练量化技术
- [[biotrain-ondevice-finetuning-mcu]] — 端侧微调
- [[ggml-llamacpp-hf]] — 端侧推理框架
