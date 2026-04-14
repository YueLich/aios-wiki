---
type: concept
tags: [gui-agent, benchmark, humanization, mobile, evaluation]
related: [[pspa-bench-gui-agent]], [[secagent-mobile-gui]], [[clawmobile-agentic]]
sources:
  - "[arXiv] Turing Test on Screen: A Benchmark for Mobile GUI Agent Humanization"
created: 2026-04-14
---

# 图灵测试屏幕版：移动 GUI Agent 拟人化基准

## 概念定义

"Turing Test on Screen" 是一个专门评估移动 GUI Agent 拟人程度的基准测试框架。它不仅仅评估任务完成率，更关注 Agent 的操作行为是否"像人"——包括点击精度、滚动节奏、界面停留时间等行为层面的相似性。

## 为什么重要

现有 GUI Agent 评估（如 [[pspa-bench-gui-agent]]）主要关注任务成功率，但忽略了用户体验维度。一个在技术上"完成任务"但操作方式令人不适的 Agent，实际部署价值有限。这个基准将评估维度从"能不能做"扩展到"做得像不像人"。

**关键发现**：
- 当前 SOTA Agent 在操作节奏上与人类有显著差异
- 过度精确的点击反而降低了用户信任度
- 拟人化的滚动和等待模式显著提升用户满意度

## 与手机端 AIOS 的关联

手机是高度个人化的设备，用户对 AI 助手的行为模式非常敏感。拟人化的 GUI Agent 能建立更好的用户信任，这是 [[clawmobile-agentic]] 等系统需要关注的新维度。未来手机 AIOS 的 Agent 框架需要在效率和拟人化之间找到平衡。

## 相关概念

- [[pspa-bench-gui-agent]] — 个性化基准，关注个性化适配
- [[secagent-mobile-gui]] — 语义上下文理解
- [[clawmobile-agentic]] — 原生 Agent 系统设计
