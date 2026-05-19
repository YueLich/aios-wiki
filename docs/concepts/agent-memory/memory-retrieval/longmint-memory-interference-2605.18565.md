---
title: "LongMINT: Evaluating Memory under Multi-Target Interference in Long-Horizon Agent Systems"
arXiv: 2605.18565
date: 2026-05-18
tags: [agent-memory, benchmark, memory-retrieval, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: 现有 agent 评测基准主要关注单任务或干净环境下的性能，忽略了真实世界中信息重复更新、跨记忆相互干扰的情况。LongMINT 填补了这一空白，首次系统性地评估 agent 在**多目标干扰**场景下的记忆表现。

### 基准设计

LongMINT 构建了三种干扰类型：

1. **覆盖干扰（Overwrite Interference）**：同一实体的信息在记忆中多次更新，后续版本覆盖前面版本
2. **关联干扰（Association Interference）**：多个相关实体的记忆在更新时产生错误关联
3. **时序干扰（Temporal Interference）**：时间敏感信息（如"今天下午的会议"）在多次交互后丢失时效性

评测环境包含 6 个领域（邮件、日历、文档、代码库、数据库、自然语言对话），每个领域设计了专门的记忆干扰注入协议。

## 核心贡献

1. **首个多目标干扰评测基准**：系统覆盖 3 类干扰、6 个领域、1200+ 评测案例
2. **揭示现有 memory-augmented agent 的关键弱点**：测试的 8 个主流 agent 在干扰场景下平均准确率下降 41%
3. **提出干扰感知评测指标**：不仅评测最终答案正确性，还追踪干扰发生时的记忆状态
4. **为未来记忆系统设计提供方向**：基于评测结果总结出抗干扰记忆系统应具备的属性

## 为什么重要

真实世界的 agent 记忆系统面临的不是"能否记住"的问题，而是"在记忆被更新/干扰时能否正确处理"的问题。LongMINT 首次将这一现实挑战引入学术评测体系，为构建更 robust 的生产级 agent 记忆系统提供了评测基础。

## 与移动端/端侧的相关性

移动端 agent 面临更密集的多应用切换和通知干扰——用户可能在导航应用中查找位置，然后收到消息打断，再切回导航。LongMINT 的评测体系直接面向这类场景，其发现的干扰弱点对端侧记忆系统设计有重要警示意义。

## 参考文献

- Lee, H., et al. (2026). LongMINT: Evaluating Memory under Multi-Target Interference in Long-Horizon Agent Systems. arXiv:2605.18565.
