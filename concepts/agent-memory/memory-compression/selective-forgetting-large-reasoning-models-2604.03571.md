---
title: "Selective Forgetting for Large Reasoning Models"
arXiv: 2604.03571
date: 2026-04-04
tags: [memory-compression, selective-forgetting, privacy, reasoning-models]
reviewer: auto
source: ArXiv RSS/API
---

# Selective Forgetting for Large Reasoning Models

## 论文基本信息

- **arXiv ID**: 2604.03571
- **作者**: Tuan Le, Wei Qian, Mengdi Huai
- **提交日期**: 2026-04-04
- **类别**: cs.AI

## 摘要

大型推理模型（LRM）在线产生思维链（CoTs）后再生成最终答案，这使得它们通过中间推理步骤特别容易受到知识泄漏的影响。然而，训练数据中敏感信息（如版权和私有内容）的记忆引发了伦理和法律问题。选择性遗忘（也称机器反学习）成为 LRMs 的潜在解决方案。但现有反学习方法的遗忘目标主要是最终答案，可能损害 LRMs 整体推理能力；直接在完整 CoTs 上反学习会破坏一般推理能力。LRM 反学习的核心挑战在于精确遗忘目标知识的同时保持一般推理能力完整性。本文提出新的 LRM 反学习框架，选择性移除敏感相关内容。

## 核心贡献

1. **LRM 特异性反学习**：首个专门针对大型推理模型（包含 CoTs）的选择性遗忘框架。
2. **CoT 中间步骤保护**：在选择性遗忘敏感内容的同时保护中间推理步骤的完整性。
3. **版权和隐私保护**：解决 LRM 通过 CoTs 泄漏敏感训练数据的问题。
4. **推理能力保护**：避免现有方法在反学习后整体推理能力下降的问题。

## 为什么重要

LRM（DeepSeek-R1、OpenAI-o1/o3 等）在业界迅速普及，其 CoTs 的隐私风险之前未被充分研究。本文首次系统处理「通过推理过程泄漏训练数据」这一新威胁。对移动端/端侧推理的意义：端侧部署的 LRMs 如果包含版权或私人数据，反学习是唯一合规出路。

## 与移动端/端侧相关性

- 端侧 LRM 部署涉及企业/个人私有数据的推理，需要选择性遗忘能力
- 移动端 App 可能在本地微调中引入版权内容，需要反学习机制
- 推理能力保护机制对端侧模型尤为重要——端侧无法通过大模型蒸馏弥补能力损失
