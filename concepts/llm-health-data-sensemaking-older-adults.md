---
type: concept
tags: [wearable, mobile-health, LLM, older-adults, self-tracking, human-computer-interaction, 可穿戴, 移动健康, LLM设计]
related: [[wearable-llm-stress-support]], [[wearable-triggered-llm-stress]], [[wearable-large-sensor-models]], [[personal-intelligence-google]]
sources:
  - url: https://arxiv.org/abs/2603.23733v1
    title: "Exploring Self-Tracking Practices of Older Adults with CVD to Inform the Design of LLM-Enabled Health Data Sensemaking"
    date: 2026-03-31
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# 老年心血管病患者自我追踪与 LLM 健康数据理解

> 基于日记研究的 LLM 健康数据理解系统设计方向

## 核心问题

可穿戴设备和移动健康 App 被越来越多地用于慢性病自我管理，但对于患有心血管疾病（CVD）的老年患者：
1. **数据过载**：自我追踪数据量大且复杂，令人不知所措
2. **解读困难**：老年人往往缺乏专业知识解读健康指标
3. **情感复杂性**：健康数据引发焦虑、希望、困惑等复杂情感反应
4. **社交动态**：与家人/医生共享数据涉及隐私和关系谈判

## 研究方法

七天日记研究 + 后续访谈：
- **参与者**：8 名 64-82 岁的 CVD 患者
- **方法**：日记记录自我追踪体验，深度访谈挖掘数据理解方式

## 六大主题发现

| 主题 | 描述 | 设计启示 |
|------|------|---------|
| 导航情感复杂性 | 数据引发焦虑、希望等混合情感 | LLM 需要情感感知，不能只提供冷冰冰的数据分析 |
| 拥有健康叙事 | 患者构建个人健康故事 | LLM 应帮助编织连贯的健康叙事，而非孤立的数据点 |
| 优先身体感受 | 身体感受优先于数字指标 | LLM 应整合主观感受与客观数据 |
| 选择性关注 | 患者选择性关注某些指标 | LLM 应尊重用户关注偏好，避免信息轰炸 |
| 分享的社会谈判 | 与家人/医生共享数据的复杂动态 | LLM 应支持可控的数据共享和沟通 |
| 对 AI 的谨慎乐观 | 对 AI 辅助既期待又担忧 | LLM 设计需要建立信任而非取代判断 |

## 关键洞察

1. **自我追踪是情感性的**：健康数据不只是数字——它嵌入在情感、社会关系和个人叙事中。LLM 健康系统需要超越数据分析，进入情感理解领域。

2. **患者代理权至上**：老年患者强调自主感——LLM 应支持而非取代患者的判断。"增强智能"而非"替代决策"的设计哲学。

3. **身体体验不可忽视**：数字指标无法完全捕捉患者的身体感受。LLM 系统应整合主观描述（如"今天胸口闷"）与客观数据（如心率曲线）。

4. **AI 信任是渐进建立的**：老年用户对 AI 有"谨慎乐观"态度——需要渐进式引入、解释性输出、可撤销的建议。

## 设计方向

LLM 健康数据理解系统应：
- **支持情感投入**：承认健康数据的情感维度，而非只关注数字趋势
- **强化患者代理权**：提供选项而非指令，让用户做最终决定
- **承认身体体验**：整合主观感受和客观数据
- **促进对话**：在临床和社交场景中促进有意义的对话

## 为什么重要

- **移动健康 AI 的设计指南**：为面向老年用户的 LLM 健康系统提供了用户研究基础
- **可穿戴 AI 的人文视角**：超越技术可行性，关注实际用户需求和情感维度
- **端侧 LLM 的应用场景**：健康数据敏感，端侧推理是必然选择——但设计必须先于技术
- **银发经济 AI 产品**：全球老龄化趋势下，面向老年用户的 AI 产品设计是重要市场

## 关联

- [[wearable-llm-stress-support]] — 可穿戴 LLM 压力支持，健康数据情感维度的直接延伸
- [[wearable-triggered-llm-stress]] — 可穿戴触发的 LLM，健康事件触发的 LLM 干预
- [[wearable-large-sensor-models]] — 可穿戴大传感器模型，健康数据采集的技术基础
- [[personal-intelligence-google]] — Google 个人智能，大公司的健康 AI 产品方向
- [[memorable-ondevice-photo-search]] — 端侧记忆化搜索，个人数据理解的端侧实现范例
- [[nanowakeword-wake-word]] — 轻量级唤醒词，健康设备的低功耗交互
