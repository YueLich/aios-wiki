---
title: "SuperLocalMemory: Privacy-Preserving Multi-Agent Memory with Bayesian Trust Defense Against Memory Poisoning"
arXiv: 2603.02240
date: 2026-02-17
tags: [agent-memory, memory-privacy, memory-security, memory-poisoning, multi-agent, local-first]
reviewer: auto
source: arXiv API
---

## 论文基本信息

- **arXiv ID**: 2603.02240
- **发表日期**: 2026-02-17
- **作者**: Varun Pratap Bhardwaj
- **方向**: 记忆隐私 / 多智能体记忆 / 记忆投毒防御
- **开源代码**: https://github.com/（MIT 许可证）

## 摘要（翻译）

本文提出 **SuperLocalMemory**，一个面向多智能体 AI 的本地优先（local-first）记忆系统，通过架构隔离和贝叶斯信任评分防御 **OWASP ASI06 记忆投毒**，同时通过自适应学习排序实现个性化检索——**无需云依赖或 LLM 推理调用**。随着 AI Agent 越来越依赖持久记忆，云端记忆系统创造了集中化攻击面，受污染的记忆会跨会话和用户传播——这一威胁已在针对生产系统的攻击中得到证实。

SuperLocalMemory 的架构结合了：SQLite + FTS5 全文搜索、Leiden 算法知识图谱聚类、事件驱动的协调层（带每 Agent 溯源）、以及自适应重排框架（通过三层行为分析学习用户偏好：跨项目技术偏好、项目上下文检测和工作流模式挖掘）。在七个基准维度上的评估表明：**10.6ms 中位搜索延迟**、10 个并发 Agent 下**零并发错误**、信任分离度（gap=0.90，sleeper attack 信任下降 72%）、自适应重排开启后 **NDCG@5 提升 104%**。行为数据隔离在独立数据库中，支持 GDPR Article 17 删除权。SuperLocalMemory（MIT）已开源，与 **17+ 开发工具**通过 Model Context Protocol 集成。

## 核心贡献

### 1. 本地优先架构
不依赖云端服务，通过 SQLite + FTS5 实现完全本地化的记忆存储和检索，消除集中化攻击面。

### 2. 贝叶斯信任评分防御
通过三层行为分析动态评估记忆条目的可信度，有效降低记忆投毒攻击的成功率（sleeper attack 信任下降 72%）。

### 3. 自适应学习排序
通过跨项目技术偏好、项目上下文检测和工作流模式挖掘三个层次，个性化检索结果，NDCG@5 提升 104%。

### 4. GDPR 合规
行为数据完全隔离，支持用户数据删除权。

### 5. Model Context Protocol 集成
与 17+ 开发工具集成，包括 GitHub、Slack、Jira 等主流开发平台。

## 为什么重要

SuperLocalMemory 是**首个完全本地化、无 LLM 推理调用的多智能体记忆系统**，从根本上消除了云端记忆的集中化攻击面。它同时解决了隐私保护、记忆投毒防御和个性化检索三个核心问题，且性能优异（10.6ms 延迟）。OWASP ASI06 将记忆投毒列为 Agent 系统的顶级威胁，SuperLocalMemory 提供了实用的工程解法。

## 与端侧/移动端的相关性

本地优先架构和 SQLite 存储非常适合端侧和移动端部署，无需网络连接即可工作。GDPR 合规和 Model Context Protocol 集成使其成为移动 AI Assistant 的理想记忆后端。10.6ms 的搜索延迟在移动设备上也完全可接受。

## 参考文献

1. See original paper for full reference list
