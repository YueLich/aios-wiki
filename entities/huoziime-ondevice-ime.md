---
type: entity
tags: [输入法, 端侧推理, LLM, 个性化, 记忆系统, 哈工大, Qwen3]
related: [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[kv-cache-quantization-ondevice]], [[llamacpp-b8831]]
sources:
  - url: https://arxiv.org/abs/2604.14159
    title: "HuoziIME: An On-Device LLM-enhanced Input Method for Deep Personalization"
    date: 2026-03-23
    reliability: high
  - url: https://github.com/Shan-HIT/HuoziIME
    title: "HuoziIME GitHub Repository"
    date: 2026-03-23
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# HuoziIME：端侧 LLM 增强的深度个性化输入法

> 哈工大提出的首个完全端侧运行、带记忆系统的生成式中文输入法，基于 Qwen3-0.6B 微调，实现隐私保护的实时个性化文本生成。

## 核心问题

当前主流 AI 输入法（SwiftKey + GPT-4、百度 + ERNIE、搜狗 + 混元等）存在三大根本局限：

1. **云优先架构**：所有 AI 功能依赖云端推理，带来延迟、离线不可用和隐私风险
2. **弱个性化**：仅有静态预设人设或基于 prompt 的浅层适配，无法学习用户真实写作习惯
3. **无持久记忆**：每次会话从零开始，无法积累用户输入历史形成深层理解

## 方法/架构

HuoziIME 采用三层架构设计：

### 1. 端侧 LLM 微调
- 基座模型：Qwen3-0.6B 系列
- 通过在合成个性化数据上进行后训练（post-training），赋予模型类人的预测能力
- 支持人设预设（persona presets）和自进化能力

### 2. 分层记忆机制（核心创新）
- **L1 短期记忆**：当前会话上下文
- **L2 中期记忆**：近期输入历史的事实提取
- **L3 长期记忆**：持久化的用户习惯和偏好
- 使用 GRPO（Group Relative Policy Optimization）增强记忆操作
- 基于 bge-small-zh-v1.5 量化模型的本地向量数据库进行检索

### 3. 系统级端侧优化
- 基于 llama.cpp 二次开发的 CPU 推理引擎
- MCP（Model Context Protocol）实现跨应用通信
- 近零延迟、严格小内存占用

## 实验结果

在联发科天玑 9000 SoC + 12GB RAM 的 Android 测试设备上：

| 测试阶段 | 成功率 |
|---------|-------|
| 记忆触发（Memory Trigger） | 99.7%（342/343） |
| 正常处理（Processing Normal） | 96.4%（163/169） |
| 拒绝处理（Processing Refusal） | 71.3%（87/122） |
| 检索 @4（Retrieval@4） | 89.5%（179/200） |
| 有根据生成（Grounded Generation） | 87.2%（156/179） |

**关键发现**：IME 的多候选特性天然补偿了轻量级嵌入模型的局限性——即使检索不完美，4 候选布局中只要命中一个就够用。

## 关键洞察

1. **输入法是端侧 LLM 最佳落地场景之一**：高频、高价值、隐私敏感，天然适合端侧部署
2. **记忆系统是输入法 AI 化的核心**：不是简单的「下一个词预测」，而是理解用户是谁、怎么写、写什么
3. **MCP 协议的实用价值**：通过标准化协议实现跨应用上下文获取，解决端侧生态碎片化问题
4. **与商业方案的差异化**：表 1 对比了 6 款主流 AI 输入法，HuoziIME 是唯一实现完全端侧 + 持久记忆 + 强个性化的方案

## 局限性

- 轻量模型推理能力受限，偶发 over-retrieval 和 retrieval-token drift
- 移动 OS 沙箱限制了实时外部应用上下文获取
- 训练语料清洗后仍可能残留偏见

## 为什么重要

HuoziIME 证明了一个重要趋势：**端侧 AI 不仅仅是推理，更可以是深度个性化的智能助手**。它的分层记忆架构对移动 AIOS 中 Agent 持久化身份设计有直接参考价值。如果输入法都能做到端侧记忆驱动的个性化，那手机上的其他 AI 交互（助手、相机、搜索）同样可以。

## 关联

- [[agent-persistent-identity]] — HuoziIME 的分层记忆系统与 Agent 持久化身份的关联
- [[mga-memory-gui-agent]] — 同样关注记忆驱动的移动 AI 交互
- [[kv-cache-quantization-ondevice]] — 端侧推理优化技术
- [[llamacpp-b8831]] — HuoziIME 基于 llama.cpp 二次开发
- [[edgeflow-cold-start]] — 端侧模型启动优化
- [[gemma4-ondevice]] — 同期发布的端侧 LLM 代表
