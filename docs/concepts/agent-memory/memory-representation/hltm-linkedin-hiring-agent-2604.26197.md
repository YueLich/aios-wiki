---
title: "HLTM: LinkedIn Hiring Agent Temporal Memory"
arXiv: 2604.26197
date: 2026-04-28
tags: [agent-memory, memory-representation]
reviewer: auto
source: arXiv RSS/API
---

# HLTM: LinkedIn Hiring Agent Temporal Memory

## 论文基本信息

- **作者**: LinkedIn AI Research 团队
- **arXiv**: https://arxiv.org/abs/2604.26197
- **领域**: cs.AI, cs.HC

## 摘要

HLTM 是 LinkedIn 招聘 Agent 的时序记忆系统，用于在长周期招聘流程中维护候选人和招聘经理的交互历史。系统处理时间跨度从几天到几个月的招聘对话，支持跨时间窗口的信息检索和推理。时序记忆使 Agent 能够记住"上次面试中候选人提到他们希望在 3 个月后换工作"这类时序约束，并据此调整沟通策略。

## 核心贡献

1. **Temporal Hiring Memory**: 首个面向招聘场景的时序 Agent 记忆系统
2. **Long-horizon Context**: 支持跨越数月招聘周期的长程上下文维护
3. **Temporal Constraint Reasoning**: 时序约束推理，支持"X 个月后"这类时间参考
4. **Multi-party Memory**: 支持候选人和招聘经理双方的多方记忆
5. **Production Scale**: 在 LinkedIn 生产环境中大规模部署验证

## 研究背景与问题

招聘是一个跨越数月的长周期流程，涉及多次面试、反馈和沟通。Agent 需要在这一长周期中维护一致的上下文，避免重复提问或遗忘关键信息。

## 核心方法

1. **Hierarchical Temporal Memory**: 分层时序记忆，支持事件、会话、项目等不同时间粒度
2. **Temporal Indexing**: 时间索引支持按时间段检索记忆
3. **Reference Resolution**: 解析和追踪"下次会议""候选人提到的 3 个月后"等时间引用
4. **Privacy-preserving Storage**: 候选人数据的隐私保护存储

## 为什么重要

HLTM 展示了时序记忆在真实生产环境（LinkedIn 招聘）中的大规模应用。对需要长周期记忆的 Agent 系统有重要参考价值。

## 与移动端/端侧相关性

1. **长周期移动场景**: 移动端 Agent（如个人助手）需要维护跨周/月的事件记忆
2. **时序约束推理**: 支持移动端任务的时序规划
3. **多方记忆**: 支持多参与者场景的记忆管理
4. **生产级验证**: 真实大规模部署验证了系统的可扩展性
