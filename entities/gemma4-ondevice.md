---
type: entity
tags: [端侧推理, Gemma, Google, MoE, 多模态, Apache 2.0, 移动端部署, agentic]
related: [[huoziime-ondevice-ime]], [[gemini-nano-chrome137]], [[mnn-350]], [[llamacpp]]
sources:
  - url: https://deepmind.google/blog/gemma-4-byte-for-byte-the-most-capable-open-models/
    title: "Gemma 4: Byte for byte, the most capable open models"
    date: 2026-04-02
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Gemma 4 — 端侧最智能的开源模型家族

> Google DeepMind 发布 Gemma 4，包含 E2B/E4B（端侧）和 26B MoE/31B Dense（桌面）四个规格，Apache 2.0 许可。端侧模型激活有效 2B/4B 参数，完全离线运行。

## 核心问题

开源模型生态在端侧存在一个根本矛盾：高能力模型（Llama 70B+、Qwen 72B）无法在手机/嵌入式设备上运行，而能在端侧运行的小模型又能力不足。Gemma 4 试图通过极致的 intelligence-per-parameter 设计解决这个矛盾。

## 方法/架构

### 四规格模型家族

| 模型 | 参数量 | 架构 | 目标硬件 | 上下文窗口 |
|------|--------|------|---------|-----------|
| E2B | 激活 2B | MoE | 手机、Raspberry Pi、Jetson Orin Nano | 128K |
| E4B | 激活 4B | MoE | 手机、平板、IoT | 128K |
| 26B MoE | 激活 3.8B | MoE | 消费级 GPU（单卡） | 256K |
| 31B Dense | 31B | Dense | H100 / 高端 GPU | 256K |

### 端侧能力矩阵（E2B/E4B）

- **原生多模态**：图像 + 视频 + 音频（E2B/E4B 特有音频输入）
- **Agentic 工作流**：原生函数调用、结构化 JSON 输出、系统指令
- **代码生成**：离线高质量代码，将工作站变为本地 AI 编程助手
- **140+ 语言**：原生多语言训练
- **完全离线**：与 Qualcomm 和 MediaTek 合作，近零延迟跨边缘设备运行
- **AICore 开发者预览**：Android 开发者可立即原型化 Agentic 流程，前向兼容 Gemini Nano 4

### Arena AI 排名（2026-04-01）

- 31B Dense：开源模型全球 #3
- 26B MoE：开源模型全球 #6
- 26B MoE 击败了 20x 大小的模型

### 生态集成

- **端侧推理**：Google AI Edge Gallery（E4B/E2B）、LiteRT-LM、llama.cpp、MLX、Ollama
- **桌面推理**：vLLM、SGLang、NVIDIA NIM
- **微调**：Hugging Face TRL、Unsloth、Google Colab、Vertex AI
- **移动端**：ML Kit GenAI Prompt API、Android Studio Agent Mode
- **协议**：Apache 2.0（商业友好）

## 关键洞察

1. **Intelligence-per-parameter 是端侧模型的核心指标**：Gemma 4 不追求参数规模，而是追求每参数的能力密度——这对端侧部署至关重要
2. **MoE 架构是端侧推理的正确选择**：26B MoE 只激活 3.8B 参数，兼顾能力与效率
3. **原生多模态 + 原生 Agent**：不是在文本模型上附加视觉/音频模块，而是原生支持——这对端侧 Agent（需要理解屏幕、语音指令）非常关键
4. **AICore + Gemini Nano 4 前向兼容**：Google 在用 Gemma 4 验证端侧 Agent 架构，为 Gemini Nano 4 做技术铺垫
5. **Apache 2.0 的战略意义**：上一代 Gemma 使用受限许可，此次改为 Apache 2.0 是对 Llama 系列开源策略的直接回应

## 为什么重要

- **端侧模型能力的新标杆**：E2B/E4B 将"手机能跑的模型"的能力上限大幅提升
- **原生 Agent 能力进入端侧**：函数调用 + 结构化输出 + 系统指令 = 端侧 Agent 的基础能力
- **多模态端侧化**：图像 + 音频的原生支持为端侧多模态 Agent 打开新可能
- **与 Qualcomm/MediaTek 深度合作**：标志着硬件厂商对端侧 AI 的重视程度进一步提升
- **Gemini Nano 4 的技术预演**：Gemma 4 E2B/E4B 很可能是 Gemini Nano 4 的技术基础

## 关联

- [[huoziime-ondevice-ime]] — HUOZIIME 使用 Qwen3-0.6B，Gemma 4 E2B 是潜在替代方案
- [[gemini-nano-chrome137]] — Gemini Nano 是 Google 的端侧推理方案，Gemma 4 可能是其开源版本
- [[mnn-350]] — MNN 是阿里端侧推理引擎，可用于部署 Gemma 4
- [[llamacpp]] — llama.cpp 已支持 Gemma 4 推理
- [[edgeflow-cold-start]] — Gemma 4 的冷启动优化是端侧部署的关键环节
