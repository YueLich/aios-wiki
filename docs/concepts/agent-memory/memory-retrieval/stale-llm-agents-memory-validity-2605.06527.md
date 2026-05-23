---
title: "STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?"
arXiv: 2605.06527
date: 2026-05-07
tags: [agent-memory, memory-retrieval, memory-validation, belief-revision]
reviewer: auto
source: arXiv API
---

## 论文信息

- **标题**: STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?
- **arXiv ID**: 2605.06527
- **作者**: Hanxiang Chao, Yihan Bai, Rui Sheng, Tianle Li, Yushi Sun
- **发表日期**: 2026-05-07
- **类别**: cs.CL

## 摘要（翻译）

大语言模型（LLM）智能体越来越需要维护连贯的长期个性化记忆，但现有基准主要衡量静态事实检索，忽略了当新证据出现时修正存储信念的能力。本文识别了一个关键且未被充分探索的失败模式——**隐式冲突（Implicit Conflict）**：后续观察会在没有显式否定的情况下使早期记忆失效，需要通过上下文推理和常识推理来检测。为了严格评估这一能力，本文提出了 STALE 基准，包含 400 个专家验证的冲突场景（跨越 100 多个日常主题，上下文最长 150K tokens，共 1,200 个评估查询），并提出三维探测框架，测试状态解析（detecting that memory is stale）、时间排序（ordering events temporally）和内容更新（updating memory content）三个维度。

## 核心贡献

1. **隐式冲突问题形式化**：首次系统定义 LLM 智能体记忆失效的隐式冲突模式——后续证据在无显式否定词的情况下使先前记忆变得过时
2. **STALE 基准**：400 个专家验证场景，1,200 个评估查询，覆盖 100+ 日常话题，上下文最长 150K tokens
3. **三维探测框架**：State Resolution（检测记忆是否过时）、Temporal Ordering（事件时间排序）、Content Update（记忆内容更新）
4. **发现**: 现有 LLM 在隐式冲突检测上存在显著不足，GPT-4o 也仅能达到 57% 的准确率，表明记忆时效性验证是重要研究方向

## 为什么重要

长期记忆系统不仅要存储信息，还需要在信息变得过时后主动识别并修正。现有 RAG 和记忆检索工作假设存储信息永久有效，忽略了真实世界知识的动态性。STALE 填补了这一空白——它揭示了当前系统在记忆时效性检测上的根本性缺陷，为下一代主动式记忆管理系统奠定了评估基础。

## 与移动端/端侧的相关性

移动端 LLM 智能体依赖本地存储的个性化记忆（对话历史、用户偏好、位置上下文），这些信息会随时间失效。STALE 揭示的隐式冲突问题在端侧场景尤为关键：设备无法持续连接云端进行实时知识更新，必须依赖本地机制判断记忆有效性。检测记忆是否过时是端侧记忆系统实现自主更新的前提。

## 参考文献

（参考文献待从原文补充）
