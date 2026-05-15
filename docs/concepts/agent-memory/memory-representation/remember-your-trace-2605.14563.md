---
title: "Remember Your Trace: Memory-Guided Long-Horizon Agentic Framework for Consistent and Hierarchical Repository-Level Code Documentation"
arXiv: 2605.14563
date: 2026-05-14
tags: [agent-memory, code-generation, hierarchical-memory]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

自动代码文档对现代软件开发至关重要，为人类开发者和编码 Agent 提供了导航大型代码库所需的上下文基础。现有的仓库级方案独立处理各个组件，导致冗余检索和文档描述冲突，且缺乏层级结构。本文提出 MemDocAgent，一个长期 Agent 框架，通过记忆机制在生成代码文档时保持一致性和层级结构。

## 核心贡献

1. **记忆引导的检索机制**：维护代码检索历史，避免重复处理相同组件，减少冗余。
2. **层级文档生成**：将代码库结构映射为树状的层级文档，保持各层级描述的一致性。
3. **跨会话记忆追踪**：记录之前会话中已处理的组件和生成的文档，新会话可继承和更新已有内容。
4. **一致性约束**：通过记忆中的上下文约束，确保同一组件在不同文档中描述一致。

## 为什么重要

代码文档是 Agent 记忆的重要载体——代码本身的结构、变更历史、依赖关系都是长期记忆。MemDocAgent 展示了如何在代码生成类 Agent 中构建结构化记忆，解决多会话场景下的知识一致性问题，对构建真正实用的代码助手具有重要意义。

## 与移动端/端侧的相关性

虽然主要面向软件开发场景，但其层级记忆和一致性维护机制可迁移到移动端文档处理、笔记整理等场景。在资源受限的端侧，层级记忆结构能更高效地利用存储空间。
