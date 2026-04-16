---
type: entity
tags: [embodied-ai, spatial-reasoning, tool-calling, robotics, gemini, multimodal, vla]
related: [[summer-multimodal-memory]], [[exectune-guide-core-policy]], [[clawmobile-agentic]]
sources:
  - url: https://deepmind.google/blog/gemini-robotics-er-1-6/
    title: "Gemini Robotics-ER 1.6: Powering real-world robotics tasks through enhanced embodied reasoning"
    date: 2026-04-14
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Gemini Robotics-ER 1.6: 增强具身推理的机器人智能

> Google DeepMind 发布的具身推理模型，通过增强空间推理和多视角理解，为机器人提供前所未有的环境感知精度。可通过 Gemini API 和 Google AI Studio 访问。

## 核心问题

机器人需要的不只是遵循指令——它们必须**推理物理世界**。从导航复杂设施到读取压力表指针，"具身推理"是连接数字智能与物理行动的桥梁。Gemini Robotics-ER 1.6 专注于解决机器人在真实环境中所需的三类核心推理能力。

## 方法/架构

### 核心能力

1. **指向（Pointing）作为空间推理基础**
   - 精确物体检测和计数
   - 关系逻辑：比较、"从A到B"关系定义
   - 运动推理：轨迹映射和最优抓取点识别
   - 约束合规：复杂提示推理（如"指向所有能放入蓝色杯子的物体"）
   - 可作为中间推理步骤处理复杂任务

2. **工具调用能力**
   - 原生调用 Google Search 获取信息
   - 调用视觉-语言-动作模型（VLA）
   - 支持第三方用户自定义函数
   - 作为机器人的高层推理模型，协调底层执行

3. **仪表读取（Instrument Reading）**——新解锁能力
   - 读取复杂仪表盘和视镜
   - 与 Boston Dynamics 合作发现的用例
   - 使用 agentic vision 实现

### 模型对比
- 对比 Gemini Robotics-ER 1.5 和 Gemini 3.0 Flash
- 空间和物理推理能力显著提升：指向、计数、成功检测
- 支持单视角和多视角成功检测

## 实验结果/关键数据

| 能力领域 | 改进幅度 |
|----------|---------|
| 指向精度 | 显著提升 |
| 计数准确性 | 显著提升 |
| 成功检测（单视角） | 显著提升 |
| 成功检测（多视角） | 新增能力 |
| 仪表读取 | 新增能力 |

开发者可通过 Gemini API 和 Google AI Studio 直接使用，并提供 Colab 示例。

## 关键洞察

1. **工具调用架构的普适性**：Gemini Robotics-ER 的"推理模型 + 工具调用"架构与手机端 Agent 的 ExecTune 框架理念一致——高层推理模型负责规划，底层工具负责执行
2. **空间推理向移动端的迁移潜力**：虽然面向机器人，但空间推理（指向、计数、关系判断）在手机端 AR 应用、屏幕理解、拍照辅助等场景有直接应用价值
3. **多视角理解**：机器人需要整合多摄像头视角，手机端多摄像头系统（主摄+超广角+长焦）同样面临多视角融合问题

## 为什么重要

1. **Agent 推理架构参考**：验证了"大型推理模型 + 专用工具"的分层架构在具身场景的有效性，手机端可借鉴类似模式
2. **空间推理能力**：虽然 Gemini Robotics-ER 面向物理机器人，但其空间推理方法论可迁移到手机端 AR/视觉理解场景
3. **工具调用标准化**：原生支持搜索、VLA 调用和第三方函数的架构为移动端 Agent 工具链设计提供了标准化参考
4. **API 可访问性**：通过 Gemini API 提供服务，移动端应用可直接集成

## 关联
- [[exectune-guide-core-policy]] — 同为"高层推理 + 底层执行"的分层架构
- [[clawmobile-agentic]] — ClawMobile 的原生 Agent 设计可整合空间推理能力
- [[summer-multimodal-memory]] — SUMMER 的多模态检索与 Gemini 的多模态推理互补
- [[dronescan-yolo]] — 无人机视觉检测可受益于 Gemini 的空间推理
