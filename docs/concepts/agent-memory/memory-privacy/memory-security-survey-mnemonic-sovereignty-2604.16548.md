---
title: "A Survey on the Security of Long-Term Memory in LLM Agents: Toward Mnemonic Sovereignty"
arXiv: "2604.16548"
date: "2026-04-17"
tags: [agent-memory, memory-privacy, security, survey]
reviewer: auto
source: arXiv ti: search
---

# A Survey on the Security of Long-Term Memory in LLM Agents: Toward Mnemonic Sovereignty

## 论文基本信息

- **arXiv ID**: 2604.16548
- **发表日期**: 2026-04-17
- **作者**: Zehao Lin, Chunyu Li, Kai Chen
- **类别**: cs.CR (Cryptography and Security)
- **来源**: arXiv ti: search

## 摘要

大语言模型安全研究正从"模型是否会泄露训练数据"转向一个更具后果性的问题：一个具有持久长期记忆的智能体是否能被持续塑造、跨会话投毒、未授权访问并在共享组织状态中传播？现有调查覆盖记忆架构和智能体机制，但较少以持久可写记忆的认知和治理属性为中心来审视记忆作为独立安全问题的原因。

本调查填补了这一空白。借鉴认知神经科学和记忆哲学，本文将智能体记忆表征为**可塑的（malleable）、可重写的（rewritable）和社会传播的（socially propagating）**，并围绕六个阶段——**写入（Write）、存储（Store）、检索（Retrieve）、执行（Execute）、遗忘（Forget）和治理（Govern）**——构建记忆生命周期框架。

## 核心贡献

1. **记忆生命周期安全框架**：首个覆盖"写入→存储→检索→执行→遗忘→治理"全周期的智能体记忆安全分析框架
2. **记忆攻击面系统梳理**：跨会话投毒（cross-session poisoning）、未授权访问、记忆传播（memory propagation）等新型威胁的分类体系
3. **认知科学与哲学基础**：引入认知神经科学和记忆哲学视角，为记忆安全提供跨学科理论支撑
4. **Mnemonic Sovereignty（记忆主权）**：提出智能体用户对自身记忆数据应有控制权的概念框架

## 为什么重要

传统 LLM 安全聚焦于训练数据泄露，但持久记忆智能体引入了一个全新维度的攻击面：
- **可塑性攻击**：记忆可以被改写（不同于静态模型权重），攻击者可通过多次交互逐步塑造智能体行为
- **跨会话传播**：共享组织记忆（如企业知识库）一旦被投毒，影响范围远超单一会话
- **遗忘的双刃剑**：遗忘机制既是隐私保护手段，也可能被用来掩盖攻击痕迹

## 与移动端/端侧的相关性

端侧智能体（如私人手机助手）存储用户高度敏感的个人信息、对话历史和行为偏好。记忆安全问题在端侧尤为关键：
- 设备丢失或被盗导致的未授权记忆访问风险
- 多用户共享设备时的记忆隔离问题
- 端侧记忆压缩/遗忘过程中的信息残留风险

## 参考文献

（详见原论文）
