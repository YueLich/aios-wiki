---
type: entity
tags: [gemini, google, llm, multimodal, reasoning, agentic, on-device]
related: [[gemma4-ondevice]], [[gemini-31-flash-lite]], [[gemini-31-deep-think]], [[gemma-4-google]]
sources:
  - url: https://deepmind.google/models/gemini/pro/
    title: "Gemini 3.1 Pro — Google DeepMind"
    date: 2026-04-19
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Gemini 3.1 Pro

> Google DeepMind 最强智能模型，具备前沿推理、多模态理解和 Agent 编码能力。定位为 Gemini 3 系列旗舰。

## 核心定位

Gemini 3.1 Pro 是 Google Gemini 3 系列中的旗舰模型，专注于复杂任务处理和创意概念实现。相比 3.1 Flash-Lite（高吞吐）和 3.1 Flash（速度优先），Pro 版本以**推理深度**为核心竞争力。

## 关键能力

### 推理与理解
- **深度推理**：在复杂问题上提供简洁、直接且有洞察力的回复，拒绝套话和谄媚
- **多模态理解**：文本、图像、视频、音频、代码——全模态统一推理
- **SOTA 推理基准**：在标准推理评测中达到业界最高水平

### Agent 与编码
- **Agent 编码**（Vibe Coding / Agentic Coding）：Gemini 3.1 在工具调用和 Agent 编码方面有显著提升
- **改进的工具使用**：更好的指令遵循能力，支持多步骤并行任务
- **Agent 能力**：可执行更智能的多步任务委托

### 实际应用
- **学习**：理解复杂主题，提供个性化解释
- **构建**：从草图和提示到交互式工具和体验
- **规划**：委托任务和多步项目，加快执行速度

## 模型系列定位

| 模型 | 定位 | 适用场景 |
|------|------|----------|
| Gemini 3.1 Deep Think | 专业推理模式 | 科学研究、数学、工程 |
| Gemini 3.1 Pro | 旗舰智能 | 复杂任务、创意编码 |
| Gemini 3 Flash | 速度优先 | 日常任务、快速响应 |
| Gemini 3.1 Flash-Lite | 高吞吐 | 大规模部署、成本敏感 |

## 对手机端 AI 的意义

Gemini 3.1 Pro 虽为云端模型，但其架构设计直接影响端侧部署策略：
1. **Agent 编码能力**可以被压缩到 Gemma 4 等端侧模型
2. **多模态推理范式**为端侧多模态 Agent 提供参考架构
3. **工具调用改进**意味着 Agent 框架在移动端的可执行性提升

## 关联
- [[gemma4-ondevice]] — Gemma 4 是 Gemini 3.1 Pro 的端侧版本
- [[gemini-31-deep-think]] — Deep Think 基于 3.1 Pro 构建的增强推理模式
- [[gemma-4-google]] — Google 官方 Gemma 4 介绍
- [[gemini-31-flash-lite]] — 轻量版 Gemini，适合端云协同
- [[agent-persistent-identity]] — Agent 编码能力依赖的持久化身份框架
