---
type: concept
tags: [小模型, Token选择, 知识蒸馏, 端侧推理, Apple]
related: [[gemma4-ondevice]], [[qwen35-small]], [[septq-post-training-quantization]], [[lcsb-finetuning-ondevice]]
sources:
  - url: https://machinelearning.apple.com/research/lacy
    title: "LaCy: What Small Language Models Can and Should Learn is Not Just a Question of Loss"
    date: 2026-04
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# LaCy：小语言模型应该学什么——超越损失函数的Token选择哲学

> Apple 机器学习团队提出的新型预训练方法，解决小语言模型 (SLM) 在端侧部署中的核心矛盾：哪些知识应该自己掌握，哪些应该委托给外部大模型。

## 核心问题

小语言模型 (SLM) 的参数容量有限，预训练能压缩的世界知识有明确上限。实践中通过让 SLM 访问外部来源（查询大模型、文档或数据库）来缓解这一问题。但一个根本性问题未被回答：**在预训练中，哪些 token SLM 应该自己学会预测，哪些应该通过 `<CALL>` token 委托给外部资源？**

## 方法/架构

### 关键发现

1. **损失值不是唯一信号**：虽然损失值可以预测预测 token 是否与 ground-truth 匹配，但某些 token 即使损失很高，也是预训练文档的**可接受替代延续**（truthful alternative continuations），不应触发 `<CALL>`。

2. **语法解析辅助判断**：spaCy 语法解析器可以帮助增强损失信号，区分：SLM 应该委托的 token（事实性错误风险高） vs 应该学习的 token（即使损失高，也是安全的替代延续）。

3. **LaCy 预训练方法**：基于上述 token 选择哲学的新型预训练流程。

### 工作机制

```
For each token position:
  1. Compute loss
  2. If loss HIGH:
     a. Use spaCy grammar parser to check if token is a valid syntactic alternative
     b. If valid alternative → LEARN (safe to predict)
     c. If likely factual error → DELEGATE (use <CALL> token)
  3. If loss LOW → LEARN normally
```

## 实验结果

- LaCy 模型成功学习了**哪些 token 自己预测，哪些需要委托**
- 在与大模型级联生成时，FactScore 显著提升
- **优于 Rho 和 LLM-judge 训练的 SLM** 方法

## 关键洞察

- **"可接受的替代延续"是关键概念**：不是所有与 ground-truth 不同的预测都是错误的。语言的多义性意味着某些高损失预测仍然是"正确的"——这颠覆了传统以损失为唯一信号的训练哲学
- **与端侧Agent的关联**：手机端 SLM 可以用 LaCy 方法训练，在大多数情况下自主处理，只在高风险事实性场景中才调用云端大模型——这本质上是一种**智能的端云协同策略**
- **Apple 的研究方向信号**：这暗示 Apple 正在深入研究如何让设备端小模型更智能地决定何时需要外部帮助

## 为什么重要

对于手机端 AIOS 而言，LaCy 提供了一个**优雅的端云协同范式**：不是简单地在端侧运行小模型或在云端运行大模型，而是让端侧模型学会"自知之明"——知道自己知道什么、不知道什么，在合适的时机委托给外部资源。这与 [[trispirit-cognitive-architecture]] 的分层推理理念和 [[on-device-vs-cloud-agentic-tool-calling]] 的端云决策高度契合。

## 关联

- [[gemma4-ondevice]] — Gemma 4 等端侧模型可从 LaCy 的 token 选择策略中受益
- [[qwen35-small]] — 小型 Qwen 模型同样面临容量限制问题
- [[septq-post-training-quantization]] — 量化和 token 选择是端侧优化的两个互补维度
- [[lcsb-finetuning-ondevice]] — LCSB 的内存高效微调与 LaCy 的选择性学习哲学一致
- [[trispirit-cognitive-architecture]] — 分层推理与 LaCy 的委托决策机制互补
