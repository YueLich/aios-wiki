---
type: entity
tags: [zuver, agentic-ai, edge-computing, 10mb, go, open-source, lightweight-agent]
related:
  - "[[native-agent-systems]]"
  - "[[mobile-ad-detection-agent]]"
  - "[[secagent-mobile-gui]]"
sources:
  - https://zuver.cc
  - https://news.ycombinator.com/item?id=47768506
created: 2026-04-14
---

# Zuver — 10MB 内存的端侧 Agent 框架

Zuver 是一个开源的 Agentic AI 框架，声称整个 Agent 系统只需 **10MB RAM** 即可运行。

## 核心卖点
- **极低内存占用**: 10MB RAM 即可运行完整的 Agent 系统
- **开源**: 开源实现，可审计和定制
- **Go 实现**: 用 Go 语言编写，无 Python 依赖，天然适合跨平台部署
- **面向企业**: 定位为 "enterprise agents"，强调可靠性和可扩展性
- **端侧优先**: "Next OS is AI" — 愿景是 AI 成为操作系统的核心层

## 为什么重要

在 [[native-agent-systems]] 和 [[secagent-mobile-gui]] 等方案中，Agent 系统通常需要 Python runtime + 大量依赖，内存占用动辄数百 MB。Zuver 的 10MB 方案如果性能可靠，将对端侧 Agent 部署产生重大影响：

1. **IoT/穿戴设备** — 10MB 意味着智能手表、TWS 耳机都能跑 Agent
2. **后台驻留** — 手机上 10MB 的后台进程几乎不影响电池和内存
3. **Go 生态** — 编译为单二进制，无 runtime 依赖，部署极简

但需注意：
- 10MB 是框架本身还是包括模型？如果模型另算，实际价值需要重新评估
- 社区关注度较低（HN 仅 3 points），成熟度待验证
- 缺乏 benchmark 数据和生产案例

## 相关
- [[native-agent-systems]] — 端侧 Agent 系统总览
- [[mobile-ad-detection-agent]] — 移动端 Agent 检测方案
- [[secagent-mobile-gui]] — 移动端 GUI Agent 安全框架
