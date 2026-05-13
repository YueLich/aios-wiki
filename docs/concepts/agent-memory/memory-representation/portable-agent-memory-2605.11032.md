---
title: "Portable Agent Memory: A Protocol for Cryptographically-Verified Memory Transfer Across Heterogeneous AI Agents"
arXiv: 2605.11032
date: 2026-05-10
tags: [agent-memory, memory-representation, privacy, security]
reviewer: auto
source: arXiv RSS/API
---

# Portable Agent Memory: 异构AI Agent间加密验证的内存Transfer协议

## 论文概览

| 字段 | 内容 |
|------|------|
| 标题 | Portable Agent Memory: A Protocol for Cryptographically-Verified Memory Transfer Across Heterogeneous AI Agents |
| 作者 | Santhosh Kumar Ravindran |
| 提交日期 | 2026-05-10 |
| 类别 | cs.CR (Cryptography and Security) |
| 论文简介 | 提出开放协议和参考实现，实现跨异构AI Agent的持久记忆状态Transfer |

## 核心贡献

### 1. 五组件结构化记忆模型
- 内容可寻址的条目结构
- **Merkle-DAG 溯源图**（provenance graph）提供篡改证据
- 支持记忆条目的完整性验证

### 2. 基于能力的访问控制（Capability-Based Access Control）
- 实现选择性、有范围的记忆披露（scoped disclosure）
- 不同Agent可以只访问其授权的记忆片段
- 保护隐私敏感的记忆内容

### 3. 抗注入的再水化协议（Injection-Resistant Rehydration Protocol）
- 将召回的内容适配到异构目标模型
- 缓解间接提示注入攻击（indirect prompt injection）
- 确保记忆在不同模型间的安全Transfer

### 4. JSON 优先序列化格式 + 可选 CBOR 紧凑格式
- JSON 格式便于调试和互操作
- CBOR 压缩格式用于高效传输

### 5. Python SDK 实现
- 54个通过的测试用例
- 多个平台的Agent技能（agent skills）
- 跨模型记忆Transfer演示（GPT-4, Claude, Gemini, Llama）

## 为什么重要

现代AI Agent积累了丰富的上下文——情景事件、语义知识、程序性技能、工作状态、身份偏好——但这些上下文被锁定在特定供应商的运行时中，无法跨平台Transfer。

本协议首次提出：
- **开放的记忆Transfer标准**
- **加密验证的完整性保证**
- **异构Agent间的隐私保护**

## 与移动端/端侧的相关性

端侧Agent（如移动端、可穿戴设备、边缘服务器）需要在不同平台间Transfer记忆：

1. **跨设备连续性**：用户在手机、平板、桌面设备间切换，记忆需要无缝Transfer
2. **隐私保护**：Merkle-DAG提供篡改证据，用户可验证记忆是否被篡改
3. **选择性披露**：能力访问控制确保只有授权方可以访问特定记忆片段
4. **抗注入安全**：再水化协议防止恶意记忆注入攻击

## 技术架构

```
记忆条目 (Content-Addressable Entry)
        ↓
  Merkle-DAG Provenance Graph
        ↓
  Capability-Based Access Control
        ↓
  Injection-Resistant Rehydration
        ↓
  JSON / CBOR Serialization
```

## 参考

- arXiv: https://arxiv.org/abs/2605.11032
