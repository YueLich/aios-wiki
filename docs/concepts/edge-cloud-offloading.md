---
type: concept
tags: [edge-computing, offloading, llm, mobile, world-model]
related: [[edge-cloud-collaboration]], [[on-device-inference]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2602.13628v1
    title: "Compact LLM Deployment and World Model Assisted Offloading in Mobile Edge Computing"
    date: 2026-02
created: 2026-04-14
---

# 紧凑 LLM 部署与世界模型辅助的移动边缘卸载

## 概述

这篇论文提出了一种结合紧凑型 LLM 部署和世界模型辅助决策的移动边缘计算卸载策略。

## 核心思路

- **紧凑模型部署**：在边缘节点部署小型 LLM（1-3B）
- **世界模型预测**：用轻量级世界模型预测任务复杂度
- **智能卸载**：基于预测结果决定在本地还是云端执行

## 为什么重要

这是 [[edge-cloud-collaboration]] 架构的重要进展。传统卸载策略基于规则或简单启发式，而世界模型辅助方法可以更准确地预判任务需求，减少不必要的网络往返。与 [[sustainability-ondevice-intelligence]] 的能耗分析结合，可以实现真正的能效最优调度。


## 核心问题

We prove an Alexandrov-Bakelman-Pucci type estimate, which involves the integral of the determinant of the complex Hessian over a certain subset. It improves the classical ABP estimate adapted (by inequality $2^{2n}|\det(u_{i\bar{j}})|^2\geq |\det(\nabla^2u)|$) to complex setting. We give an application of it to derive sharp gradient estimates for complex Monge-Ampère equations. The approach is based on the De Giorgi iteration method developed by Guo-Phong-Tong for equations of complex Monge-Ampère type.

## 为什么重要

本研究/产品对手机端 AIOS 生态有重要参考价值。推动端侧 AI 从概念走向实际部署。

## 关联

- [[edge-cloud-collaboration]] — 端云协同整体架构
- [[mnn]] — 边缘推理框架
- [[edgeflow-cold-start]] — 本地模型启动优化
