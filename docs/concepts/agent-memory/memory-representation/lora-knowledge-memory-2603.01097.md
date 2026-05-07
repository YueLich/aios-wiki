---
title: Understanding LoRA as Knowledge Memory - An Empirical Analysis
arXiv: 2603.01097
date: 2026-03-01
tags: [agent-memory, knowledge-memory, LoRA, continual-learning]
reviewer: auto
source: arXiv API
---

# Understanding LoRA as Knowledge Memory: An Empirical Analysis

## 摘要

大模型的持续知识更新越来越必要，但仍然具有挑战性。虽然推理时方法（如 In-Context Learning 和 RAG）很流行，但它们受上下文预算、成本和检索碎片化约束。本文研究使用低秩适应（LoRA）作为模块化知识记忆的参数化方法。实验表明，LoRA 可以有效编码不同类型的知识，其记忆容量与秩和层位置相关，且可以与 RAG 等非参数化方法互补。

## 核心贡献

1. **LoRA 作为知识记忆的实证框架**：系统研究 LoRA 的知识存储特性
2. **知识容量分析**：发现 LoRA 的记忆容量与秩大小和层位置相关
3. **知识类型敏感性**：不同类型知识（事实、推理、程序）对 LoRA 编码的敏感性不同
4. **LoRA + RAG 混合系统**：参数化和非参数化记忆的协同机制
5. **遗忘特性**：LoRA 知识记忆的稳定性和可遗忘性分析

## 技术方法

### 实验设计
- 在多种知识类型上测试 LoRA 的编码能力
- 控制秩大小、层位置、训练步数等变量
- 对比 LoRA 记忆与 RAG 的检索质量

### 关键发现
1. **秩的选择**：高秩 LoRA 编码更多细节，低秩适合抽象知识
2. **层位置**：不同层编码不同类型的知识（浅层编码语法，深层编码语义）
3. **与 RAG 的互补**：RAG 处理高频访问知识，LoRA 处理长尾知识
4. **遗忘机制**：可通过调整秩实现选择性遗忘

## 为什么重要

这是将"知识记忆"从非参数化（外部存储）扩展到参数化（模型权重）的重要工作。对于 Agent 系统，这意味着记忆不一定非要从外部检索，也可以通过轻量微调的方式"记住"——就像人类既能用工作记忆（快速）也能用长期记忆（深刻）。

## 与移动端/端侧相关性

1. **LoRA 作为端侧记忆**：在移动设备上用 LoRA 存储个性化知识
2. **模块化知识管理**：不同用户的知识用不同 LoRA 模块隔离
3. **隐私保护**：参数化知识更难被直接提取
4. **高效推理**：知识"内化"到权重中，减少推理时检索开销

## 参考文献

- Seungju Back, Dongwoo Lee, Naun Kang, Taehee Lee. "Understanding LoRA as Knowledge Memory: An Empirical Analysis." arXiv:2603.01097, 2026.
