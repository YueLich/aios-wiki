---
type: concept
tags: [mobile-aios, overview, 系统综述]
related: []
created: 2026-04-18
updated: 2026-04-18
---

# Mobile AIOS 全景概述

> 概念页面 — 从多个相关页面的 wikilink 引用自动创建

手机端 AI 操作系统（Mobile AIOS）是指在智能手机等移动设备上原生集成 AI 能力的操作系统层设计。

## 核心范畴

- **端侧推理引擎**: llama.cpp、MNN、coremltools 等将模型部署到手机芯片
- **AI 原生 OS**: 小米 HyperAI、华为 HarmonyOS AI、三星 Galaxy AI 在系统层面集成 AI Agent
- **端侧 Agent**: 在手机上运行的 AI 助手，具备 GUI 操作、工具调用、记忆管理能力
- **隐私与端云协同**: 敏感数据本地处理，复杂任务云端协同

## 关键技术栈

| 层次 | 技术 | 代表 |
|------|------|------|
| 模型 | 端侧 LLM、多模态 | Gemma 4、Qwen3.6、MiniCPM |
| 推理 | 量化、剪枝、蒸馏 | KV-Cache 量化、SEPTQ |
| 调度 | 端云路由、模型选择 | RPRA、LaCy |
| 硬件 | NPU、GPU、DSP | Apple Neural Engine、Qualcomm Hexagon |

## 关联

- [[clawmobile-agentic]] — 原生 Agent 系统架构
- [[edge-cloud-offloading]] — 端云协同卸载
- [[septq-post-training-quantization]] — 后训练量化
- [[gemma4-ondevice]] — 端侧多模态模型
- [[sustainability-ondevice-intelligence]] — 可持续性权衡
