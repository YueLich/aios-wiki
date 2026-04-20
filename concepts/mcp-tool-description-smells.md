---
type: concept
tags: [MCP, 工具描述, Agent效率, 工具调用, 模型上下文协议]
related: [[on-device-vs-cloud-agentic-tool-calling]], [[exectune-guide-core-policy]], [[mana-mobile-ad-detection]]
sources:
  - url: https://arxiv.org/abs/2602.14878
    title: "MCP Tool Descriptions Are Smelly! Towards Improving AI Agent Efficiency with Augmented MCP Tool Descriptions"
    date: 2026-02-20
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# MCP 工具描述存在质量问题

> 对 856 个 MCP 工具的实证分析发现 97.1% 的描述存在至少一个"异味"（arXiv:2602.14878）

## 核心问题

Model Context Protocol (MCP) 定义了 Foundation Model 基础 agent 如何通过调用工具与外部系统交互。但 FM 依赖**自然语言工具描述**来理解工具的目的和功能——这些描述的质量直接影响 agent 选择最优工具和传递正确参数的能力。

## 方法/架构

研究分析了 **103 个 MCP 服务器上的 856 个工具**：

1. 从文献中识别出工具描述的 **6 个组成部分**
2. 开发基于这些组件的**评分量表**
3. 基于评分量表形式化定义**工具描述异味（smells）**
4. 使用 FM 驱动的扫描器进行量化评估

## 实验结果

| 指标 | 数据 |
|------|------|
| 分析工具数 | 856 |
| MCP 服务器数 | 103 |
| 存在至少一个异味 | **97.1%** |
| 未说明目的 | 56% |

## 关键洞察

工具描述异味会误导 FM-based agent，导致：
- **工具选择错误**：agent 选择不恰当的工具
- **参数传递错误**：agent 给工具传递错误的参数
- **任务失败**：因为工具使用不当导致整体任务失败

## 为什么重要

在手机端 Agent 场景中，MCP 是 agent 与设备功能（相机、定位、通讯录等）交互的关键协议。如果工具描述存在质量问题，端侧 Agent 的工具使用能力将大打折扣。本研究揭示了 MCP 生态中的系统性质量问题，为改进端侧 Agent 工具调用提供了实证依据。

## 关联
- [[on-device-vs-cloud-agentic-tool-calling]] — 工具描述质量影响端侧/云端工具调用选择
- [[exectune-guide-core-policy]] — Guide Model 的工具使用策略受工具描述质量影响
- [[mana-mobile-ad-detection]] — MANA 的多模态工具调用也依赖高质量工具描述
- [[mcp-deployment-patterns]] — MCP 部署模式需考虑工具描述质量
