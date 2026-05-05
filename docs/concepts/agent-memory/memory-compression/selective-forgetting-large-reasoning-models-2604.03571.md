---
title: "Selective Forgetting for Large Reasoning Models"
arXiv: 2604.03571
date: 2026-04-04
tags: [agent-memory, memory-compression]
reviewer: auto
source: arXiv RSS/API
---

# Selective Forgetting for Large Reasoning Models

**作者:** Tuan Le, Wei Qian, Mengdi Huai  
**发表:** 2026-04-04

## 摘要

Large Reasoning Models (LRMs) generate structured chains of thought (CoTs) before producing final answers, making them especially vulnerable to knowledge leakage through intermediate reasoning steps. Yet, the memorization of sensitive information in the training data such as copyrighted and private content has led to ethical and legal concerns. To address these issues, selective forgetting (also known as machine unlearning) has emerged as a potential remedy for LRMs. However, existing unlearning methods primarily target final answers and may degrade the overall reasoning ability of LRMs after forgetting. Additionally, directly applying unlearning on the entire CoTs could degrade the general reasoning capabilities. The key challenge for LRM unlearning lies in achieving precise unlearning of targeted knowledge while preserving the integrity of general reasoning capabilities. To bridge this gap, we in this paper propose a novel LRM unlearning framework that selectively removes sensitive reasoning components while preserving general reasoning capabilities. Our approach leverages multiple LLMs with retrieval-augmented generation (RAG) to analyze CoT traces, identify forget-relevant segments, and replace them with benign placeholders that maintain logical structure. We also introduce a new feature replacement unlearning loss for LRMs, which can simultaneously suppress the probability of generating forgotten content while reinforcing structurally valid replacements. Extensive experiments on both synthetic and medical datasets verify the desired properties of our proposed method.

## 核心贡献

（待补充：本文的核心创新点和方法论）

## 为什么重要

（待补充：本文在领域中的重要性和影响）

## 与端侧/移动端相关性

（待补充：本文方法对端侧部署的意义）

## 关键文献

（待补充：相关工作和引用）
