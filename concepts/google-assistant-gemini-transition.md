---
type: concept
tags: [Google, Gemini, assistant, mobile-ai, transition, architecture, agent]
related: [[personal-intelligence-google]], [[gemini-31-flash-live]], [[experimental-hybrid-inference-android]], [[edgeflow-cold-start]], [[gemini-deep-think]]
sources:
  - url: https://9to5google.com/2026/04/18/what-is-happening-with-the-google-assistant-video/
    title: "What is happening with the Google Assistant?"
    date: 2026-04-18
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# Google Assistant → Gemini 迁移：从规则引擎到 LLM Agent 的范式转换

> Google 正在终结运行十年的 Google Assistant，用 Gemini 取代其在 Android、Chromebook、Android Auto 和智能家居中的位置。这不仅是产品更迭，而是从"if-this-then-that"确定性架构到 LLM 驱动推理架构的根本性转变。

## 核心问题

Google Assistant 自 2016 年发布以来，基于**刚性规则引擎**（确定性 if-this-then-that 逻辑）构建。它擅长执行原子级微任务（设闹钟、播音乐、控制智能家居），但无法理解上下文、无法处理模糊指令、无法进行多轮推理。随着 LLM 时代的到来，这种确定性架构成为"上一个时代的遗物"。

## 迁移时间线

- **2024年初**：Google 砍掉 18 项 Assistant 功能（管理菜谱、语音重新安排日历事件等）
- **2026年3月**：Android 设备上 Assistant 不再是可选项，Gemini 成为默认
- **2026年3月**：第二波"使用率低"功能被移除
- **2026年4月**：Chrome OS 134 开始过渡到 Gemini；Android Auto 开始广泛部署 Gemini

## 被移除的关键功能

| 功能 | 状态 | 影响范围 |
|------|------|---------|
| 多媒体控制（收藏/分享照片、查询位置） | 移除 | 手机 |
| Photo Frame 语音命令 | 移除 | 智能显示设备 |
| Interpreter Mode（实时翻译模式） | 大幅削减 | 跨设备 |
| Family Bell（家庭提醒） | 移除/手动化 | 智能家居 |
| Driving Mode（驾驶模式） | 日落 | Android Auto |
| LG webOS TV Assistant | 关闭 | 智能电视 |
| Fitbit Sense 2/Versa 4 Assistant | 移除 | 可穿戴设备 |

## 架构差异：Assistant vs Gemini

**Google Assistant** 是为**微任务**设计的——即时、可靠地执行单一小任务。其核心是"效用优先"（Utility-First）哲学。

**Gemini** 是为**宏推理**设计的——复杂对话、上下文理解、多步推理。它能用自然语言处理模糊输入，但代价是：
- **延迟更高**：云端推理需要"思考时间"，在驾驶场景（70mph）下可能危及安全
- **不确定性**：有时给出令人沮丧的结果，不像 Assistant 的确定性响应
- **过度复杂**：用户只想说"Hey Google, 开灯"时，Gemini 的叠加界面显得笨重

## 关键洞察

1. **"数字衰败"（Digital Decay）现象**：Google 通过服务端更新逐步移除已购硬件的功能，暴露了"硬件即服务窗口"的商业模式风险。购买智能显示屏用于数字相框功能的用户，在功能被远程移除后感到被"违约"。

2. **信任赤字**：Assistant 的逐步萎缩不是中性事件——它在迫使用户迁移的同时，破坏了对 Google 生态系统的信任。

3. **驾驶场景的延迟安全问题**：Assistant 的本地命令（"打电话给妈妈"、"导航回家"）执行极快；Gemini 的云端推理产生延迟，在高速驾驶中可能造成安全隐患。Google 需要在 Assistant 的速度和 Gemini 的智能之间找到平衡。

4. **端侧推理的紧迫性**：这一迁移案例完美说明了为什么端侧推理（on-device inference）对移动 AI 至关重要——云端延迟在实时交互场景（驾驶、语音控制）中不可接受。[[edgeflow-cold-start]] 和 [[experimental-hybrid-inference-android]] 正是在解决这个问题。

## 为什么重要

对手机端 AI 生态而言，这标志着**AI 助手范式的根本转折**：
- 从命令式交互 → 对话式交互
- 从确定性执行 → 概率性推理
- 从本地处理 → 云端/端云协同处理
- 从单一功能 → 全能 Agent

这一转变带来了新的技术挑战：端侧推理延迟、模型压缩需求（[[kv-cache-quantization-ondevice]]）、Agent 身份持久化（[[agent-persistent-identity]]），以及隐私保护（端侧数据不外传的必要性）。

## 关联

- [[personal-intelligence-google]] — Google 在移动 AI 助手方面的另一项重要功能（Personal Intelligence toggle）
- [[gemini-31-flash-live]] — Gemini 语音交互的核心模型
- [[experimental-hybrid-inference-android]] — 解决 Gemini 云端延迟的端云混合推理方案
- [[edgeflow-cold-start]] — 端侧模型冷启动优化，直接缓解迁移延迟问题
- [[agent-persistent-identity]] — 从 Assistant 到 Gemini 的迁移也涉及 Agent 身份和记忆的连续性问题
- [[gemini-deep-think]] — Gemini 的高级推理能力，代表了 Assistant 完全无法实现的新范式
