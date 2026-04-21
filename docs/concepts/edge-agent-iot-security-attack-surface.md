---
type: concept
tags: [edge-agent, iot-security, llm-agent, mqtt, systems-security, attack-surface, 边缘安全]
related: [[agent-persistent-identity]], [[gui-agent-privacy]], [[on-device-vs-cloud-agentic-tool-calling]], [[aagenttee-confidential-agent]]
sources:
  - url: https://arxiv.org/abs/2602.22525
    title: "Systems-Level Attack Surface of Edge Agent Deployments on IoT"
    date: 2026-04-20
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# 边缘 Agent 部署的系统级攻击面分析

> 帝国理工学院团队对 LLM Agent 在 IoT 设备上边缘部署的安全性进行了实证分析，识别了 5 种系统级攻击面，包括两种在实时测试中发现的新兴故障模式。arXiv: 2602.22525

## 核心问题

将 LLM Agent 部署到 IoT 设备的边缘节点（如手机、智能家居设备）时，安全性问题与云端部署截然不同。云端有成熟的安全基础设施（身份认证、网络隔离、日志审计），而边缘环境引入了全新的攻击面，但缺乏系统性的安全分析。

## 方法/架构

### 三种部署架构对比
1. **纯云端 (Cloud-hosted)**: Agent 全部在云端运行
2. **边缘本地集群 (Edge-local swarm)**: 多个设备上的 Agent 通过本地 MQTT 消息协作
3. **混合架构 (Hybrid)**: 本地推理 + 云端回退

### 测试环境
- 多设备家庭自动化测试平台
- 本地 MQTT 消息传递
- Android 智能手机作为边缘推理节点

### 5 种系统级攻击面
1. **数据泄露**: 边缘本地部署消除了常规云端数据暴露
2. **协调状态发散 (Coordination-state divergence)**: 多 Agent 协作时的状态不一致——**在实时测试中发现的新兴故障**
3. **信任侵蚀 (Induced trust erosion)**: 恶意诱导 Agent 降低对其他 Agent 的信任——**在实时测试中发现的新兴故障**
4. **主权边界完整性**: 回退机制触发时，部署边界在应用层不可见地跨越
5. **溯源链完整性**: 协作操作下溯源链完整，但无加密强制时可被绕过

### 可度量的安全指标
- 数据外泄量 (Data egress volume)
- 故障切换窗口暴露 (Failover window exposure)
- 主权边界完整性 (Sovereignty boundary integrity)
- 溯源链完整性 (Provenance chain completeness)

## 实验结果/关键数据

- 边缘本地部署消除了常规云端数据暴露风险
- 但回退机制触发时**静默降级**主权边界——在应用层完全不可见
- 溯源链在协作操作下完整，但缺乏加密强制时可被轻易绕过
- 故障切换窗口创建瞬态盲区，可被利用进行未授权操作

## 关键洞察

1. **边缘部署不是"更安全"那么简单**: 消除云端数据暴露的同时，引入了全新的攻击面——协调状态发散和信任侵蚀是传统安全模型完全没考虑过的

2. **静默降级是最危险的**: 边缘→云端回退时的主权边界跨越在应用层完全不可见——用户以为数据在本地，但实际上已经发到了云端

3. **部署架构是安全的第一决定因素**: 不是模型设计、不是提示词工程，而是**部署架构本身**决定了安全风险水平

4. **MQTT 本地通信的隐患**: 本地 MQTT 消息看似安全（不经过互联网），但缺乏加密时很容易被局域网内攻击者截获和篡改

## 为什么重要

对手机端 AIOS 的核心意义：
- **手机作为边缘推理节点的安全性**: 手机是最常见的边缘 Agent 节点——作为智能家居控制中心、个人助理、数据聚合器，其安全架构设计至关重要
- **端云回退的隐私透明性**: 手机端 Agent 常常需要云端回退（如本地模型能力不足时），用户需要清楚知道数据何时离开了设备
- **多 Agent 协作的安全性**: 未来的手机 AIOS 可能运行多个 Agent（个人助理、健康管理、智能家居），它们之间的协作需要安全的协调协议
- **硬件安全基础**: TEE（可信执行环境）和硬件加密可以解决溯源链绕过问题——这是端侧部署的天然优势

## 关联
- [[agent-persistent-identity]] — Agent 身份和状态管理
- [[gui-agent-privacy]] — GUI Agent 的隐私保护
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端的架构选择
- [[aagenttee-confidential-agent]] — 基于 TEE 的机密 Agent 执行
- [[edgecim-hardware-codesign]] — 边缘硬件协同设计中的安全考量