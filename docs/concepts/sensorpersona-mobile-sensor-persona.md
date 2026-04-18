---
type: concept
tags: [llm, personalization, mobile-sensors, continual-learning, persona-extraction, on-device]
related: [[lifedialbench-lifelog-memory]], [[agent-persistent-identity]], [[mga-memory-gui-agent]], [[companion-knowledge-mobile-agent]]
sources:
  - url: http://arxiv.org/abs/2604.06204
    title: "SensorPersona: An LLM-Empowered System for Continual Persona Extraction from Longitudinal Mobile Sensor Streams"
    date: 2026-03-15
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# SensorPersona: 基于LLM的移动传感器持续人格提取系统

> 从手机传感器的长期连续数据流中持续推断稳定用户人格特征，实现真正的行为驱动个性化

## 核心问题

现有LLM Agent的个性化主要依赖聊天历史来推断用户画像（persona），但这种方式只能捕获用户主动披露的信息，无法反映用户在物理世界中的真实行为模式。手机传感器（加速度计、GPS、陀螺仪等）每时每刻都在记录用户的运动、位置和活动数据，这些数据蕴含着丰富的行为语义，但缺乏系统性的利用方法。

## 方法/架构

SensorPersona是一个三层架构系统：

### 1. 面向个人的上下文编码（Person-Oriented Context Encoding）
- 对连续传感器流进行语义增强，将原始传感器数据转化为有意义的上下文描述
- 处理多模态传感器数据（GPS轨迹、活动识别、屏幕使用模式等）

### 2. 层次化人格推理（Hierarchical Persona Reasoning）
- **片段内推理（Intra-Episode Reasoning）**：从单次传感器事件中提取局部行为模式
- **片段间推理（Inter-Episode Reasoning）**：跨多个时间片段整合行为模式，形成稳定的人格特征
- 利用LLM的推理能力从传感器语义中推断深层用户偏好

### 3. 持续学习机制（Continual Learning）
- 系统能够在时间推移中不断更新和完善用户人格模型
- 处理用户行为漂移（behavioral drift）和长期习惯变化
- 人格特征的稳定性与动态性的平衡

## 实验结果

- 在真实用户手机传感器数据上验证
- 从连续传感器流中提取的人格特征相比纯聊天历史推断具有更高的稳定性和覆盖面
- 推断的人格可有效提升下游Agent任务的响应质量

## 关键洞察

**传感器是最未被充分利用的个性化信号源**。每部手机每天产生GB级的传感器数据，但这些数据主要被用于计步器、导航等单一功能。SensorPersona的创新在于将这些数据视为一种"行为日志"，通过LLM的语义理解能力，从中提取出深层的人格画像。

**持续性 vs 一次性**：与传统的用户画像一次性构建不同，SensorPersona强调持续更新。用户的行为和偏好会随时间变化，系统需要跟踪这种变化而非静态定义。

## 为什么重要

对手机端AI生态而言，SensorPersona代表了一种新的个性化范式：
1. **被动数据优于主动输入**：用户不需要告诉AI自己的偏好，AI通过观察行为就能推断
2. **隐私友好**：所有处理可以在设备端完成，无需上传原始传感器数据
3. **长期价值**：随使用时间增长，人格模型越来越准确，形成正反馈循环
4. **Agent人格基础**：为移动Agent提供持久化的用户理解能力，是实现真正个性化Agent的关键组件

## 关联
- [[lifedialbench-lifelog-memory]] — 日志记忆是传感器人格提取的数据基础
- [[agent-persistent-identity]] — Agent需要理解用户人格才能形成有效的持久化身份
- [[mga-memory-gui-agent]] — 记忆驱动的GUI Agent可利用传感器人格提升决策
- [[companion-knowledge-mobile-agent]] — 陪伴知识系统可以整合传感器推断的人格
- [[lacy-small-model-token-selection]] — 小模型选择策略与传感器数据处理的效率考量
