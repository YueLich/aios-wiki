---
title: "Selective Forgetting for Large Reasoning Models"
arXiv: 2604.03571
date: 2026-04-04
authors: ["Tuan Le", "Wei Qian", "Mengdi Huai"]
tags: [agent-memory, memory-compression, selective-forgetting, machine-unlearning, privacy, large-reasoning-models]
reviewer: auto
source: arXiv API
---

## 论文信息

- **arXiv**: 2604.03571
- **作者**: Tuan Le, Wei Qian, Mengdi Huai
- **提交日期**: 2026-04-04
- **方向**: 选择性遗忘 / 机器unlearning / 隐私

## 摘要（全文翻译）

大型推理模型（LRM）在产生最终答案前先生成结构化思维链（CoTs），这使得它们特别容易通过中间推理步骤泄露知识。同时，训练数据中敏感信息（版权内容和私有内容）的记忆引发伦理和法律担忧。

选择遗忘（又称机器 unlearning）已成为 LRM 的一种潜在解决方案。然而现有 unlearning 方法主要针对最终答案，可能损害 LRM 的整体推理能力。直接对整个 CoTs 应用 unlearning 会损害一般推理能力。

LRM unlearning 的关键挑战在于：在精确遗忘目标知识的同时，保持一般推理能力的完整性。

## 核心贡献

1. **LRM unlearning 框架**：选择性遗忘目标知识，同时保持一般推理能力
2. **针对 CoT 的精确遗忘**：不是对整个模型 unlearning，而是精确到敏感推理步骤
3. **保持推理完整性**：遗忘后的一般推理能力不退化
4. **隐私 + 版权保护**：解决 LRM 通过推理链泄露训练数据的问题

## 为什么重要

随着 LRMs（OpenAI o1/o3、DeepSeek-R1 等）越来越普及，它们的推理链泄露问题变得严重。CoT 的每一步都暴露了模型从训练数据中记忆的信息。Selective Forgetting 为 LRM 时代的隐私保护提供了新思路。

## 与端侧/移动端的相关性

端侧部署的 LRM（如手机上的小型推理模型）需要能够"忘记"某些敏感记忆，而不影响整体推理能力。这对个人设备上的隐私保护有直接意义。
