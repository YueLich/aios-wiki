---
type: concept
tags: [human-ai-interaction, agent-design, transparency, cooperation, HCI, mobile-agent, 人机交互, Agent架构]
related: [[mobile-aios-overview]], [[on-device-vs-cloud-agentic-tool-calling]], [[agent-persistent-identity]], [[sustainability-ondevice-intelligence]], [[gemma4-ondevice]]
sources:
  - url: https://arxiv.org/abs/2604.15607
    title: "Imperfectly Cooperative Human-AI Interactions: Comparing the Impacts of Human and AI Attributes in Simulated and User Studies"
    date: 2026-04-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# 不完美合作的人机交互：AI 透明性 vs 人类个性的影响

> 一项比较模拟数据与真实用户研究的因果发现分析，揭示 AI 设计特性（尤其是透明性）在真实人机交互中远比人类个性特质更具影响力。

## 核心问题

在人机交互场景中，AI 设计特征（适应性、专业性、透明性）和人类个性特质（外向性、宜人性）各自如何影响交互质量？在目标不完全一致的"不完美合作"场景中（如招聘谈判、信息交易），二者的相对影响力如何？

现有研究大多只关注模拟环境或单一场景，缺乏对模拟 vs 真实人类被试的系统性比较。

## 方法/架构

研究采用**双轨对比设计**：

### 实验场景
1. **招聘谈判**：人类求职者与 AI 招聘代理谈判
2. **AI-LieDar 交易**：AI 代理可能隐瞒信息以最大化内部目标的交易场景

### 干预变量
- **人类侧**：Extraversion（外向性）、Agreeableness（宜人性）
- **AI 侧**：Adaptability（适应性）、Expertise（专业性）、Chain-of-thought Transparency（思维链透明性）

### 数据规模
- 模拟实验：2,000 次模拟
- 用户研究：290 名人类被试
- 分析方法：因果发现分析（SEM + 热力图）

## 实验结果/关键数据

### 核心发现：模拟 vs 真实的分歧

| 维度 | 模拟实验 | 用户研究 |
|------|---------|---------|
| 主导因素 | 人格特质 | AI 设计特征 |
| 透明性影响 | 中等 | **强烈但效果混合** |
| 宜人性效果 | 增强关系性沟通 | 较弱 |
| 外向性效果 | 正向影响对话温度 | 较弱 |

### 关键定量发现

- **模拟环境**：人格特质操纵占主导地位，Extraversion 对对话温度和情感评分产生强烈正向影响
- **真实用户**：AI 特质（尤其是透明性）产生最强且最一致的效果
- **透明性的双面性**：增强客观 LLM 评分指标，但效果并非完全正面——不同场景下表现分化
- **宜人性悖论**：在模拟中增强沟通但在谈判中降低得分（Points scored 降低）

### 场景差异
招聘谈判和 AI-LieDar 交易场景之间存在显著结果分歧，说明人机交互设计需要场景特定的策略。

## 关键洞察

1. **模拟不能替代真实研究**：纯模拟实验高估了人格特质的影响，低估了 AI 设计特征的作用。这对依赖模拟评估 AI agent 的研究方法论构成挑战。

2. **透明性是最具杠杆效应的 AI 设计维度**：在真实用户交互中，chain-of-thought 透明性比适应性和专业性更具影响力。这意味着移动 AIOS agent 应优先投资透明性设计。

3. **不完美合作场景需要专门设计**：当人和 AI 目标不完全一致时（现实中常见），通用的"助手"设计模式不够——需要考虑目标冲突下的交互策略。

4. **人格特质的影响被高估**：虽然个性确实影响交互，但在真实场景中其影响力远小于 AI 侧的设计决策。

## 为什么重要

对手机端 AIOS 生态的意义：

- **Agent 透明性设计**：移动 AI agent（如小米 HyperAI、苹果 Apple Intelligence）应优先考虑推理过程的透明展示，而非仅追求个性化适配
- **评估方法论**：纯模拟基准测试不足以评估 agent 交互质量，需要真实的用户研究验证
- **场景特定设计**：手机端 agent 在不同场景（购物、搜索、日程管理）中应采用差异化的合作策略
- **隐私与信任**：透明性影响信任——在手机端隐私敏感场景中尤为关键

## 关联

- [[mobile-aios-overview]] — 手机端 AIOS 整体架构，人机交互是核心层
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用中的透明性差异
- [[agent-persistent-identity]] — Agent 持久化身份如何影响用户信任和交互质量
- [[sustainability-ondevice-intelligence]] — 端侧智能的可持续性权衡
- [[gemma4-ondevice]] — 端侧模型的推理透明性实现
