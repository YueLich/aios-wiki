---
type: concept
tags: [mobile, ad-detection, multimodal, agent, ui-navigation, security, 模型]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]]
sources:
  - "[arXiv] MANA: Towards Efficient Mobile Ad Detection via Multimodal Agentic UI Navigation"
created: 2026-04-14
---

# MANA：多模态 Agent 驱动的移动广告检测

## 概念定义

MANA（Multimodal Agentic Navigation for Ad detection）利用多模态 Agent 通过 UI 导航来检测移动应用中的广告。不同于传统的静态分析（无法处理动态加载的广告），MANA 使用 Agent 主动探索界面，通过视觉理解和交互判断来识别广告内容。

## 为什么重要

移动广告是 App 变现的核心模式，但也带来严重问题：
- **用户体验**：侵入式广告打断用户流程
- **安全风险**：恶意广告可能传播恶意软件
- **检测挑战**：静态分析无法应对动态加载、个性化投放的广告

MANA 的创新在于用 Agent 来对抗 Agent（广告 SDK 的智能投放），形成了一种"Agent vs Agent"的检测范式。

## 与手机端 AIOS 的关联

手机 AIOS 的安全子系统可以从 MANA 获得启发——Agent 不仅能执行用户指令，还能主动检测和防御威胁。结合 [[secagent-mobile-gui]] 的语义理解能力和 [[clawmobile-agentic]] 的原生执行能力，可以构建更智能的手机安全防护。

## 相关概念

- [[secagent-mobile-gui]] — GUI Agent 语义理解
- [[pspa-bench-gui-agent]] — Agent 基准测试
- [[clawmobile-agentic]] — 原生 Agent 系统

## 核心问题

This work presents a two-stage physics-informed, data-driven constitutive modeling framework for hyperelastic soft materials undergoing progressive damage and failure. The framework is grounded in the concept of hyperelasticity with energy limiters and employs Gaussian Process Regression (GPR) to separately learn the intact (undamaged) elastic response and damage evolution directly from data. In Stage I, GPR models learn the intact hyperelastic response through volumetric and isochoric response functions (or only the isochoric response under incompressibility), ensuring energetic consistency of the intact response and satisfaction of fundamental principles such as material frame indifference and balance of angular momentum. In Stage II, damage is modeled via a separate GPR model that learn

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[clawmobile-agentic]] — Agent 系统架构
- [[mnn-350]] — 推理引擎
- [[kv-cache-quantization-ondevice]] — 内存优化
