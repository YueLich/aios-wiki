---
type: concept
tags: [agent, confidential-computing, edge, tee, on-device, llm-agent, privacy]
related: [[zero-egress-psychiatric-ai]], [[edge-cloud-offloading]], [[gui-agent-privacy]]
sources:
  - url: https://arxiv.org/abs/2604.18231
    title: "AgenTEE: Confidential LLM Agent Execution on Edge Devices"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# AgenTEE: 边缘设备上的机密 LLM Agent 执行

> 利用可信执行环境（TEE）在边缘设备上安全运行 LLM Agent，实现隐私保护的自主推理与工具调用。arXiv: 2604.18231

## 核心问题

LLM Agent 需要处理大量敏感用户数据（对话历史、个人偏好、API 密钥等），但现有部署方案要么依赖云端推理（数据离开设备），要么在本地以明文形式处理数据（面临恶意软件和侧信道攻击风险）。在企业级和高安全场景中，这构成了严重的隐私与合规障碍。

## 方法/架构

AgenTEE 提出了一种基于 **ARM TrustZone TEE** 的机密 Agent 执行框架，核心设计包括：

### 1. 安全执行分区
- 将 Agent 的推理循环、工具调度和状态管理全部移入 TEE 安全世界（Secure World）
- 普通世界（Normal World）仅负责 UI 交互和网络 I/O，无法访问 Agent 内部状态
- LLM 权重和 KV Cache 均在安全世界内解密和计算

### 2. 机密工具调用
- Agent 对外部工具的调用通过 TEE 内的安全通道执行
- API 密钥和认证令牌仅存在于安全世界内存中
- 工具返回结果在进入普通世界前可选择性脱敏

### 3. 轻量化适配
- 针对边缘设备（手机、IoT 网关）的资源约束进行了优化
- 使用量化 LLM（INT4/INT8）降低 TEE 内存压力
- 安全世界与普通世界之间的上下文切换开销控制在 <5ms

## 实验结果

论文在多种边缘设备上评估了 AgenTEE 的性能：

| 指标 | 纯本地（无 TEE） | AgenTEE (TEE) | 开销 |
|------|-----------------|---------------|------|
| 推理延迟 | 1x | 1.08-1.15x | 8-15% |
| Token 吞吐量 | 1x | 0.87-0.93x | 7-13% 下降 |
| 安全世界内存 | N/A | +120-250MB | 可接受 |
| 工具调用延迟 | 1x | 1.05x | <5ms 额外 |

**关键发现**：
- TEE 内的推理性能开销主要来自内存加密（AES-CTR），而非计算受限
- 在 Snapdragon 8 Gen 3 和 Exynos 2400 上，安全世界能流畅运行 3B 参数量化的 LLM
- 多工具并发调用场景下，TEE 的隔离性反而减少了竞态条件导致的错误

## 关键洞察

AgenTEE 的核心贡献在于证明了 **TEE 并非 LLM Agent 的瓶颈**。传统观点认为 TEE 内存和计算受限，不适合运行 AI 工作负载，但通过以下优化策略：
1. **分层安全**：仅将最敏感的组件（推理核心、密钥管理）放入 TEE
2. **流式解密**：模型权重按需从加密存储解密到安全世界，避免一次性加载全部权重
3. **异步工具调用**：外部工具调用异步执行，不阻塞推理循环

这使得 TEE 成为边缘 Agent 部署的实用安全方案，而非理论上的理想化设计。

## 为什么重要

对手机端 AIOS 生态的意义：
- **企业市场准入**：金融机构、医疗保健、政府机构可以合规地在员工手机上部署 AI Agent
- **用户信任**：即使手机被 root 或感染恶意软件，Agent 处理的数据仍受 TEE 保护
- **混合部署基础**：TEE 可作为端云协同的安全锚点——敏感数据在 TEE 内处理，非敏感计算可卸载到云端
- **硬件趋势契合**：ARM CCA（Confidential Compute Architecture）和 Qualcomm SPUR 正在普及，为 AgenTEE 提供硬件基础

## 关联
- [[zero-egress-psychiatric-ai]] — 同为隐私保护的端侧 AI 部署方案，但侧重医疗场景
- [[edge-cloud-offloading]] — AgenTEE 的安全通道可扩展为安全的端云卸载机制
- [[gui-agent-privacy]] — GUI Agent 的隐私保护需要类似的 TEE 隔离机制
- [[kv-cache-quantization-ondevice]] — TEE 内内存受限，KV Cache 量化是关键优化
