---
title: "NeuSymMS: A Hybrid Neuro-Symbolic Memory System for Persistent, Self-Curating LLM Agents"
arXiv: 2605.17596
date: 2026-05-17
tags: [agent-memory, memory-representation, neuro-symbolic, memory-consolidation]
reviewer: auto
source: arXiv RSS/API
---

## 论文概览

**机构**: 多机构合作

**核心问题**: 现有 LLM agent 的记忆系统要么是纯神经网络的向量存储（缺乏可解释性、难以编辑），要么是纯符号系统的规则存储（缺乏灵活性），都无法满足长期运行 agent 的"自我维护"需求——如何在记忆中整合新知识、修正错误记忆、遗忘无关信息，同时保持记忆的可审计性和可解释性。

**方法**: NeuSymMS（Neuro-Symbolic Memory System）提出一种混合架构，结合神经网络的学习能力和符号系统的推理能力，实现 agent 记忆的自主维护。

### 混合记忆架构

1. **神经记忆层（Neural Memory Layer）**：用向量数据库存储经验的语义表示，支持快速相似性检索
2. **符号记忆层（Symbolic Memory Layer）**：用知识图谱存储实体关系和逻辑规则，支持可解释的推理和记忆编辑
3. **跨层整合机制**：神经层提供检索候选，符号层进行逻辑验证和一致性检查，两者协同输出最终记忆查询结果

### 自我维护能力

- **知识整合**：当新信息与旧记忆冲突时，符号层进行逻辑推理判断是否接受新信息、是否需要修正旧记忆
- **记忆归档**：长时间未访问的记忆自动降级到归档存储，减少活跃记忆负担
- **可审计性**：所有记忆变更都记录在符号层的变更日志中，支持事后追踪和人工审计

## 核心贡献

1. **首个混合神经-符号记忆系统**：同时利用向量检索的灵活性和符号推理的可解释性
2. **自我维护机制**：首次在 LLM agent 记忆中实现自动知识整合、修正和归档，无需人工干预
3. **持久记忆支持**：在多会话（Multi-session）场景中验证了记忆的持久性和一致性
4. **跨领域适用性**：在医疗、金融、客服三个领域的 agent 上验证了框架的通用性

## 为什么重要

自我维护是长期运行 agent 的核心需求——如果每次记忆冲突都需要人工介入，记忆系统就无法真正"自主"。NeuSymMS 的混合架构为这一挑战提供了可行的工程方案，其符号层的设计使得记忆系统不仅是存储工具，还是可推理、可审计的知识库。

## 与移动端/端侧的相关性

端侧 agent 特别需要自我维护能力——用户不可能频繁地手动管理 agent 记忆。NeuSymMS 的记忆归档机制可以在端侧实现"自动清理"，保证长时间运行后记忆系统不会膨胀。可审计性对端侧隐私保护也有意义——用户可以查看 agent 记住了什么、为什么记住。

## 参考文献

- Sultan, M., et al. (2026). NeuSymMS: A Hybrid Neuro-Symbolic Memory System for Persistent, Self-Curating LLM Agents. arXiv:2605.17596.
