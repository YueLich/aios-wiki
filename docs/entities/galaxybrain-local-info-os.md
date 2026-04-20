---
type: entity
tags: [local-first, information-os, on-device, file-management, ai-assistant]
related: [[agent-persistent-identity]], [[on-device-inference-memory-pressure]]
sources:
  - url: https://galaxybrain.com
    title: "GalaxyBrain — An Information Operating System"
    date: 2026-04-20
    reliability: medium
  - url: https://news.ycombinator.com/item?id=43805391
    title: "Show HN: GalaxyBrain"
    date: 2026-04-20
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# GalaxyBrain: 本地文件驱动的信息操作系统

> 一个以本地文件为核心的信息操作系统，通过 AI 理解和组织用户个人文件。

## 核心理念

GalaxyBrain 将用户的本地文件（文档、笔记、代码等）作为知识源，
通过 AI 模型理解和索引这些文件，构建一个以个人信息为中心的操作系统。
这与传统的云端 AI 助手不同——所有处理都在本地完成。

## 为什么重要

对于手机端 AIOS 生态，GalaxyBrain 代表了一种重要的范式：

1. **本地优先 (Local-First)**: 不依赖云端，所有 AI 推理在设备上完成
2. **隐私保护**: 用户数据不离开设备，符合端侧 AI 的隐私承诺
3. **个人信息理解**: 手机上积累的大量个人数据（照片、消息、文档）需要
   类似的本地 AI 来理解和组织
4. **端侧知识图谱**: 将碎片化的个人信息组织成可用的知识结构

## 技术方向

- 文件级语义理解与索引
- 本地向量数据库存储
- 端侧 LLM 推理用于问答和检索
- 跨应用信息关联

## 对手机端 AIOS 的启示

手机是用户最大的个人信息载体。GalaxyBrain 的理念可以应用于：
- 相册智能整理（不只是按时间，而是按语义）
- 跨应用搜索（消息+邮件+文档联合检索）
- 个人知识助手（基于本地数据的问答）

## 关联
- [[agent-persistent-identity]] — Agent 如何维护用户个人知识状态
- [[on-device-inference-memory-pressure]] — 端侧推理的内存约束
- [[llamacpp]] — 可用的端侧推理引擎
