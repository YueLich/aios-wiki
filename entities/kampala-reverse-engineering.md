---
type: entity
tags: [reverse-engineering, mitm-proxy, api-extraction, mobile-app, agent-tooling, yc-w26]
related: [[mcp-deployment-patterns]], [[gui-agent-user-interface]], [[on-device-vs-cloud-agentic-tool-calling]]
sources:
  - url: https://www.zatanna.ai/kampala
    title: "Kampala by Zatanna — MITM Proxy for Reverse Engineering"
    date: 2026-04-19
    reliability: medium
  - url: https://news.ycombinator.com/item?id=47774971
    title: "Launch HN: Kampala (YC W26) – Reverse-Engineer Apps into APIs"
    date: 2026-04-19
    reliability: medium
created: 2026-04-19
updated: 2026-04-19
---

# Kampala: 将移动应用逆向工程为 API

> Kampala (YC W26, Zatanna 出品) 是一个 MITM 代理工具，可以拦截任意移动/桌面应用的 HTTP/S 流量，自动追踪认证链，并将捕获的工作流导出为可复用的自动化 API——让 AI Agent 能与任何应用交互。

## 核心问题

AI Agent 要在手机上真正"操作应用"，最大的障碍不是推理能力，而是**接入能力**。绝大多数移动应用没有开放 API，Agent 只能通过 GUI 点击（如 [[gui-agent-user-interface]] 方案）或 Accessibility 服务交互。但 GUI 操作脆弱且慢——一个 UI 更新就可能导致 Agent 失效。Kampala 提出了另一条路：**从网络层逆向出隐藏 API**。

## 方法/架构

- **全流量拦截**：实时捕获任意应用/浏览器的 HTTP/S 请求
- **认证链自动追踪**：映射 token、cookie、session 和多步认证序列
- **工作流录制与回放**：捕获操作序列，导出为稳定自动化
- **TLS 指纹保持**：拦截后的流量保持原始 HTTP/TLS 指纹，避免被服务端检测为机器人
- **平台支持**：macOS 已发布，Windows waitlist

## 关键洞察

**Agent 工具链的"缺失环节"**：[[mcp-deployment-patterns]] 定义了 Agent 如何调用工具，[[a2a-protocol]] 定义了 Agent 间如何通信，但"如何从无 API 的应用中提取 API"一直是个空白。Kampala 填补了这个空白。

**端侧 vs 云端**：Kampala 本身是端侧工具（在用户设备上运行 MITM），提取出的 API 可以供端侧 Agent 直接调用，不需要云端中转。这与 [[on-device-vs-cloud-agentic-tool-calling]] 的端侧工具调用理念一致。

**局限性**：MITM 代理需要安装根证书，对证书固定 (Certificate Pinning) 的应用无效。且导出的 API 是"脆弱"的——服务端更新可能改变接口。

## 为什么重要

1. **降低 Agent 接入门槛**：不需要等待应用开发商开放 API，Agent 可以通过逆向工程接入任意应用
2. **YC W26 背书**：表明逆向工程 + Agent 自动化是一个被投资人认可的方向
3. **移动 Agent 生态补充**：与 GUI Agent 方案（[[gui-agent-user-interface]]）形成互补——GUI 方案更通用但脆弱，API 方案更稳定但需要逆向

## 关联

- [[mcp-deployment-patterns]] — Agent 工具调用模式，Kampala 提供的是工具发现层
- [[gui-agent-user-interface]] — GUI Agent 方案，Kampala 是网络层替代方案
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧工具调用，Kampala 提取的 API 可在端侧直接调用
- [[secagent-mobile-gui]] — 移动 GUI Agent，与 Kampala 的 API 提取形成技术路线对比
