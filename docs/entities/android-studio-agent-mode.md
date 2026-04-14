---
type: entity
tags: [android, agent, developer-tools, on-device, ai-assistant, 平台]
related: [[clawmobile-agentic]], [[secagent-mobile-gui]]
sources:
  - https://android-developers.googleblog.com/2026/04/Increase-Guidance-and-Control-over-Agent-Mode-with-Android-Studio-Pand
created: 2026-04-14
---

# Android Studio Agent Mode（Panda 3）

## 概述
Android Studio Panda 3 版本增强了 Agent Mode 功能，为开发者提供更多指导和控制选项。Agent Mode 允许 AI 助手自主完成代码编写、测试和调试任务。

## 核心功能
- **增强的 Agent 控制**：开发者可以更精细地控制 Agent 的行为范围
- **多设备交互测试**：配合 Android Emulator 支持多设备场景测试
- **更安全的 Agent 模式**：新增的安全护栏和确认机制

## 为什么重要
- Agent Mode 从"辅助编写代码"进化为"自主执行开发任务"
- 与 [[clawmobile-agentic]] 和 [[secagent-mobile-gui]] 共同展示了 Agent 在移动生态中的渗透
- Google 将 Agent 概念深入开发者工具链，培养开发者对 Agent 的熟悉度
- 为未来 Android 设备上更复杂的 AI Agent 场景铺路

## 对手机 AIOS 的影响
- 开发者工具中的 Agent 体验 → 移动端 Agent 框架成熟 → 用户端 AI Agent 应用爆发
- Android 17 的 Agent 安全机制直接影响手机端 AI Agent 的能力边界

## 核心问题

While Supervised Fine-Tuning (SFT) and Rejection Sampling Fine-Tuning (RFT) are standard for LLM alignment, they either rely on costly expert data or discard valuable negative samples, leading to data inefficiency. To address this, we propose Reward Informed Fine-Tuning (RIFT), a simple yet effective framework that utilizes all self-generated samples. Unlike the hard thresholding of RFT, RIFT repurposes negative trajectories, reweighting the loss with scalar rewards to learn from both the positive and negative trajectories from the model outputs. To overcome the training collapse caused by naive reward integration, where direct multiplication yields an unbounded loss, we introduce a stabilized loss formulation that ensures numerical robustness and optimization efficiency. Extensive experim

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[mnn-350]] — 推理引擎
- [[kv-cache-quantization-ondevice]] — 内存优化
