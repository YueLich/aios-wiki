---
title: "Oracle Poisoning: Corrupting Knowledge Graphs to Weaponise AI Agent Reasoning"
arXiv: "2605.09822"
date: "2026-05-10"
tags: [agent-memory, memory-security, knowledge-graph, adversarial]
reviewer: auto
source: arXiv RSS/API
---

# Oracle Poisoning: Corrupting Knowledge Graphs to Weaponise AI Agent Reasoning

## 论文基本信息

- **arXiv ID**: 2605.09822
- **发表日期**: 2026-05-10
- **作者**: Ben Kereopa-Yorke, Guillermo Diaz, Holly Wright, Reagan Johnston, Ron F. Del Rosario, Timothy Lynar
- **方向**: 记忆安全 / 知识图谱对抗
- **类别**: cs.CR

## 摘要（翻译）

本文定义了 Oracle Poisoning 一种攻击类别，攻击者腐败 AI 智能体在运行时通过工具使用协议查询的结构化知识图谱，通过正确推理导致错误结论。与提示注入不同，Oracle Poisoning 操纵的是智能体推理所依据的数据，而非其指令。本文在 4200 万节点的生产代码知识图谱上演示了六种攻击场景，首次提供了针对生产规模智能体系统的知识图谱中毒的实证演示。

## 核心贡献

1. **Oracle Poisoning 攻击框架**：定义了一种新的攻击向量——通过腐败知识图谱来武器化 AI 智能体推理
2. **六种攻击场景**：在 4200 万节点生产代码知识图谱上验证了攻击可行性
3. **跨模型评估**：在三个提供商的九个模型上进行了真实 SDK 工具使用评估
4. **传递模式揭示**：发现模型信任呈现离散断点，在 L2 攻击者复杂度下所有模型 100% 信任被污染数据
5. **交付模式作为一阶混淆因素**：内联评估产生假阴性——GPT-5.1 在内联模式下显示 0% 信任，但在模拟和真实智能体工具使用下显示 100%
6. **五种防御评估**：只读访问控制消除了直接 mutation 向量，其余四种防御是部分且模型依赖的

## 为什么重要

Oracle Poisoning 揭示了智能体记忆系统的一个根本性安全漏洞：当智能体依赖外部知识图谱进行推理时，攻击者可以通过腐败知识图谱来操控智能体的行为，而智能体仍会通过"正确的推理"得出"错误的结论"。这对于部署在边端的智能体系统尤其危险，因为边端知识图谱可能来自多个不受信任的来源。

## 与移动端/端侧相关性

- 边端智能体常依赖外部知识图谱作为记忆来源，Oracle Poisoning 揭示了这类架构的脆弱性
- 知识图谱中毒攻击比 prompt 注入更难检测，因为智能体在"正确地推理错误的数据"
- 需要新的信任验证机制来应对知识图谱来源的不可信性

## 参考文献

见原论文
