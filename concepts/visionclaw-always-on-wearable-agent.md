---
type: concept
tags: [Agent, 可穿戴AI, 多模态, 感知, 执行, 眼镜AI]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]], [[agent-persistent-identity]]
sources:
  - url: https://the-decoder.com/always-on-ray-ban-meta-glasses-powered-by-openclaw-speed-up-everyday-tasks-in-new-study/
    title: "Always-on Ray-Ban Meta glasses powered by OpenClaw speed up everyday tasks in new study"
    date: 2026-04-19
    reliability: medium
created: 2026-04-20
updated: 2026-04-20
---

# VisionClaw — 持续感知的可穿戴 Agent 系统

> 科罗拉多大学、光州科学技术院和 Google 研究团队联合提出 VisionClaw——一种始终开启的 Agent 系统，将智能眼镜的持续第一人称感知与数字任务自动执行相结合。

## 核心问题

当前 AI Agent 和智能眼镜各自为政：
- **数字 Agent**（如 OpenClaw）能操作软件、执行网页任务，但「看不见」物理世界
- **智能眼镜**（如 Ray-Ban Meta）通过摄像头和麦克风持续感知环境，但缺乏自主行动能力
- 两者之间的断层导致：用户需要手动将视觉信息转述给 Agent，体验割裂

## 方法/架构

VisionClaw 系统架构：

```
Ray-Ban Meta 眼镜（无屏幕）
    ├── 持续流式音频
    ├── 持续抓取周围环境帧
    └── 蓝牙 → 智能手机 App
                    ↓
            Gemini Live（多模态处理）
                    ↓
            OpenClaw Agent（工具调用）
                    ├── 浏览器操作
                    ├── 邮件/日历管理
                    ├── 网络搜索
                    └── 结果回传至 Gemini → 语音反馈
```

### 关键组件

1. **Ray-Ban Meta 眼镜**：无屏幕设计，持续采集音频和视频帧
2. **Gemini Live**：处理多模态输入（视觉+语音），理解上下文
3. **OpenClaw Agent**：执行数字任务的 Agent 框架，调用浏览器、邮件、日历等工具
4. **自定义手机 App**：连接眼镜与 AI 系统的桥接层

## 实验设计

研究团队进行了两项用户研究：

**研究一：系统对比（12 参与者）**
- 对比三种配置：
  - VisionClaw（持续感知 + Agent 执行）
  - 纯感知版（仅 Ray-Ban Meta + Gemini Live，无 Agent 能力）
  - 手机版（OpenClaw 在手机上，无眼镜感知）
- 评估维度：任务完成率、用户满意度、使用频率

**研究二：实际使用模式**
- 用户在日常生活中使用 VisionClaw
- 收集使用日志和访谈数据
- 分析「始终开启」AI 如何改变人机交互习惯

## 关键洞察

1. **感知+行动的统一是关键突破**：当 AI 能「看到」物理世界并自主执行任务时，用户交互模式发生质变——从主动指令转变为被动辅助
2. **持续感知 vs 隐私**：始终开启的摄像头引发隐私担忧，需要在系统层面解决
3. **多模态 Agent 的新范式**：Agent 不再局限于屏幕操作，而是通过眼镜「具身化」到物理环境
4. **可穿戴 + Agent = 交互革命**：用户无需拿出手机或电脑，AI Agent 通过眼镜成为「隐形助手」

## 为什么重要

VisionClaw 代表了手机端 AIOS 的下一个前沿方向：

1. **从手机到眼镜**：端侧 AI 的下一个硬件载体是可穿戴设备，Ray-Ban Meta 只是起点
2. **Agent 具身化**：VisionClaw 首次将 Agent 的「感知」和「执行」能力统一在可穿戴设备上
3. **持续感知范式**：与传统「按需唤醒」AI 不同，VisionClaw 始终在线、持续感知上下文
4. **混合架构**：端侧（眼镜）采集 + 云端（Gemini）理解 + Agent（OpenClaw）执行，典型的端云协同模式

对手机端 AIOS 生态：VisionClaw 可视为 [[clawmobile-agentic]] 的可穿戴延伸——从「手机上的 Agent」进化为「眼镜上的 Agent」。与 [[secagent-mobile-gui]] 和 [[pspa-bench-gui-agent]] 互补：前者关注屏幕交互的 GUI Agent，后者关注可穿戴场景的环境感知 Agent。

## 关联

- [[clawmobile-agentic]] — ClawMobile 原生 Agent 架构，VisionClaw 的设计灵感来源
- [[secagent-mobile-gui]] — 移动端 GUI 安全 Agent，对比 VisionClaw 的非屏幕交互模式
- [[pspa-bench-gui-agent]] — GUI Agent 基准测试，VisionClaw 需要新的可穿戴场景评测
- [[agent-persistent-identity]] — Agent 持久化身份，VisionClaw 需要跨设备的身份连续性
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用，VisionClaw 的混合架构案例
- [[emommas-edge-negotiation]] — 边缘多 Agent 协调，未来可穿戴 Agent 系统的协作场景
