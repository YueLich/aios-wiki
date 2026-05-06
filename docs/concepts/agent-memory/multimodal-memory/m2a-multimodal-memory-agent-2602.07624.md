---
title: "M2A: Multimodal Memory Agent with Dual-Layer Hybrid Memory for Long-Term Personalized Interactions"
arXiv: 2602.07624
date: 2026-02-07
tags: [agent-memory, multimodal-memory, personalization, hybrid-memory, long-term-interaction]
reviewer: auto
source: arXiv API
---

## 论文信息

- **作者**: Junyu Feng, Binxiao Xu, Jiayi Chen, Mengyu Dai, Cenyang Wu, Haodong Li, Bohan Zeng et al. (Little-Fridge)
- **提交日期**: 2026-02-07
- **方向**: 多模态记忆 / 个性化 / 长期交互

## 摘要

当前个性化多模态模型 predominantly 静态——概念在初始化时固定，在交互过程中无法演进。当对话历史跨越数周乃至数月、超过上下文窗口时，现有机制难以持续吸收和利用用户的增量概念、别名和偏好。

M2A提出了一种**双层混合记忆系统**，通过在线更新维护个性化多模态信息。系统采用两个协作Agent：
- **ChatAgent**：管理用户交互，自主决定何时查询或更新记忆
- **MemoryManager**：将来自ChatAgent的记忆请求分解为双层记忆库上的详细操作

双层记忆库耦合了**RawMessageStore**（不可变对话日志）和**SemanticMemoryStore**（高层观测），在不同粒度上提供记忆。

## 核心贡献

1. **双层混合记忆架构**：RawMessageStore（原始对话日志）+ SemanticMemoryStore（高层语义观测），兼顾保真度和抽象能力
2. **协作式双Agent设计**：ChatAgent（交互管理）+ MemoryManager（记忆操作），自主决定记忆读写时机
3. **可复用数据合成管道**：从Yo'LLaVA和MC-LLaVA注入概念级会话到LoCoMo长对话，保持时间一致性
4. **在线更新机制**：将个性化从一次性配置转变为共同演化的记忆机制
5. **SOTA性能**：在长期多模态交互中显著超越基线

## 方法详解

### 问题背景
现有个性化系统在初始化后概念固定，无法从交互中持续学习。当对话历史超过上下文窗口时，模型遗忘早期偏好和别名。

### 核心方法
1. **RawMessageStore**：不可变存储，记录原始对话内容，保证信息不丢失
2. **SemanticMemoryStore**：从原始对话中提取高层语义观测（用户偏好、习惯、关键事件）
3. **ChatAgent**：根据当前对话上下文，自主判断是否需要查询记忆或写入新记忆
4. **MemoryManager**：接收ChatAgent的请求，转化为对双层记忆的具体操作

### 与移动端/端侧的相关性
M2A的双层架构对移动端友好：
- **RawMessageStore**可在本地加密存储，用户隐私不外泄
- **SemanticMemoryStore**是高层抽象，存储量小，适合移动端资源限制
- 在线更新机制无需全量重训练，适合边缘部署

## 为什么重要

M2A展示了将**个性化从静态配置转化为动态记忆机制**的可能性。对于长期运行的端侧Agent（如手机助手、可穿戴设备），能够随时间学习用户偏好而不遗忘历史对话，是提升用户体验的关键。

## 参考文献

- M2A GitHub: https://github.com/Little-Fridge/M2A
