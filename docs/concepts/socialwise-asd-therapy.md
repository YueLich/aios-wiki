---
type: concept
tags: [agent, healthcare, multimodal, llm-application, autism, whisper, therapy]
related: [[whisper-ondevice]], [[multimodal-fusion]], [[agent-persistent-identity]]
sources:
  - url: https://arxiv.org/abs/2604.15347
    title: "SocialWise: LLM-Agentic Conversation Therapy for Individuals with ASD"
    date: 2026-04-20
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# SocialWise: LLM-Agent 对话疗法

> 基于 LLM Agent 的自闭症谱系障碍对话训练系统，支持多模态交互和检索增强反馈

## 核心问题

自闭症谱系障碍（ASD）影响全球超 7500 万人，约 40% 的成年自闭症患者从未获得过有偿就业。现有的社交技能训练（SST）虽然有效，但受限于成本、地理位置和治疗师资源。低成本活动（如故事阅读）效果有限，AR 工具仍需治疗师监督。

**核心需求**：需要一个无需专业人士实时指导、能提供真实角色扮演和个性化反馈的可扩展方案。

## 方法/架构

SocialWise 是一个浏览器端应用，核心架构包含三个组件：

1. **LLM 对话引擎**：基于 GPT-4o-mini 驱动场景化角色扮演对话
2. **检索增强知识库**（RAG）：检索治疗文档为反馈提供专业依据
3. **多模态接口**：支持文本和语音交互，使用 OpenAI Whisper 进行语音识别（STT）和语音合成（TTS）

### 工作流程
- 用户选择场景（如点餐、社交对话）
- 通过文本或语音与 LLM Agent 进行角色扮演
- 系统实时生成结构化反馈，对齐 ASD 沟通目标
- 整个交互周期在 3 分钟内完成

## 实验结果

- 初步用户研究（N=34）：
  - 感知有用性评分：**4.15 / 5**
  - 推荐意愿：**100%**
- 对比基线：传统故事阅读、AAC 工具、AR 辅助系统

## 关键洞察

- **LLM 替代治疗师可行性**：LLM Agent 可以提供接近治疗师水平的角色扮演训练，突破地理和成本限制
- **RAG 保证专业性**：不是纯 LLM 自由发挥，而是用治疗文档约束和指导反馈内容
- **多模态交互降低门槛**：语音交互对 ASD 用户更自然，Whisper STT/TTS 使能无缝切换

## 为什么重要

- 展示了 LLM Agent 在 **医疗健康领域** 的实际应用范式
- 多模态 + RAG 的架构模式可迁移至其他 **端侧 AI 助手** 场景
- 未来如果模型小型化，可实现完全 **离线/端侧运行** 的治疗辅助工具
- 对手机端 AI 健康助手的 **隐私保护** 设计有参考价值

## 关联
- [[whisper-ondevice]] — Whisper 语音识别的端侧部署方案
- [[multimodal-fusion]] — 多模态融合技术
- [[agent-persistent-identity]] — Agent 持久化身份与个性化
- [[edge-cloud-offloading]] — 端云协同架构
