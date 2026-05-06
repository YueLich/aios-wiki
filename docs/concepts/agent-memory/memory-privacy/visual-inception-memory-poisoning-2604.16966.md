---
title: "Visual Inception: Memory Poisoning Attacks on Vision-Language Models"
arXiv: 2604.16966
date: 2026-04-18
tags: [agent-memory, memory-privacy]
reviewer: auto
source: arXiv RSS/API
---

# Visual Inception: Memory Poisoning Attacks on Vision-Language Models

## 论文基本信息

- **作者**: Yifan Zhao, et al.
- **arXiv**: https://arxiv.org/abs/2604.16966
- **领域**: cs.CV, cs.AI

## 摘要

视觉语言模型（VLM）通过视觉 token 与语言模型的结合实现多模态理解。Visual Inception 研究了针对 VLM 的记忆污染攻击——攻击者通过在训练数据中植入特定的视觉模式，使 VLM 在推理时对特定图像产生错误的语言描述，从而实现对多模态记忆的操控。攻击利用 VLM 对抗样本的脆弱性，设计难以被人类察觉但能操控模型记忆的图像模式。

## 核心贡献

1. **Memory Poisoning Attack**: 首个针对 VLM 多模态记忆的污染攻击框架
2. **Visual Inception Patterns**: 难以察觉但能操控记忆的视觉模式
3. **VLM-specific Attack Surface**: 识别 VLM 相对于纯语言模型的独特攻击面
4. **Attack Effectiveness Analysis**: 系统分析攻击对不同 VLM 架构的有效性
5. **Defense Implications**: 揭示多模态记忆安全的独特挑战

## 研究背景与问题

传统对抗攻击针对模型输出（分类、检测），记忆污染攻击针对模型的内部记忆。VLM 的多模态特性创造了独特的攻击面——攻击者可以通过图像而非文本操控模型的信念。

## 核心方法

1. **Adversarial Visual Pattern Generation**: 生成能触发特定记忆更新的对抗视觉模式
2. **Multimodal Memory Manipulation**: 操控 VLM 对特定图像-文本对的记忆
3. **Stealth Evaluation**: 评估攻击的隐蔽性（人类感知 vs 模型响应）
4. **Cross-architecture Transfer**: 攻击在不同 VLM 架构间的可迁移性

## 为什么重要

Visual Inception 揭示了多模态 Agent 记忆系统的独特安全威胁。攻击者可以通过图像而非文本污染 Agent 的记忆，这对依赖视觉记忆的 Agent 系统（如视觉助手、机器人）有重要安全启示。

## 与移动端/端侧相关性

1. **移动端视觉 Agent**: 手机摄像头、AR 眼镜等设备的视觉记忆面临污染风险
2. **隐私敏感场景**: 视觉记忆中的个人隐私信息可能被攻击者利用
3. **本地模型风险**: 端侧 VLM 部署后难以检测记忆污染
4. **防御需求**: 端侧需要轻量级防御机制来检测记忆污染
