---
type: concept
tags: [gui-agent, privacy, mobile, anonymization, pii, multimodal, security]
related: [[gui-agent-privacy]], [[secagent-mobile-gui]], [[cora-mobile-gui-safety]], [[turing-test-mobile-gui]]
sources:
  - url: https://arxiv.org/abs/2602.10139
    title: "Anonymization-Enhanced Privacy Protection for Mobile GUI Agents: Available but Invisible"
    date: 2026-02-08
    reliability: high
  - url: https://github.com/one-step-beh1nd/gui_privacy_protection
    title: "Code Repository"
    date: 2026-02-08
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Anonymization-Enhanced Privacy Protection for Mobile GUI Agents

> 一种"可用但不可见"的匿名化框架，在保留移动 GUI Agent 任务执行能力的同时，阻止云端模型接触真实敏感信息。
>
> 来源：Zhao et al., 2026-02-08, arXiv:2602.10139

## 核心问题

移动 GUI Agent（如基于 MLLM 的自动化操作工具）在执行任务时需要捕获整个屏幕内容（截图 + XML 层级），这导致**系统性过度采集**：用户的手机号、地址、聊天记录、验证码、金融信息等敏感数据被不必要地暴露给云端模型。更严重的是，像 AppCopilot 等系统会将提取的用户信息持久缓存到内部模块，进一步扩大攻击面。

现有四类防御方案均存在根本缺陷：
| 方案类型 | 代表工作 | 核心问题 |
|---------|---------|---------|
| 暴露减少 | CORE | 仍会传输任务相关的原始敏感内容 |
| 混淆扰动 | DualTAP | 对任务相关隐私内容减弱扰动，保留可识别性 |
| 访问控制 | PrivWeb | 授权后直接暴露真实敏感值 |
| 语义替换 | GUIGuard | Agent 失去使用被掩码 PII 的能力 |

**核心矛盾**：如何让 Agent 能"使用"敏感数据完成任务，但永远"看不到"真实值？

## 方法/架构

论文提出**"可用但不可见"（Available-but-Invisible）**匿名化框架，在手机与云端 Agent 之间插入可信本地隐私层：

### 四层架构

1. **PII Detector** — 使用 PII 感知识别模型检测 UI 内容中的敏感信息（手机号、地址、邮箱、金融信息等），支持截图和 XML 层级双模态检测。

2. **UI Transformer** — 将检测到的敏感内容替换为**确定性、类型保留的占位符**（如 `PHONE_NUMBER#a1b2c`）。关键设计：
   - 占位符保留语义类别（PHONE_NUMBER、EMAIL 等）
   - 同一敏感值在会话内始终映射到同一占位符（一致性）
   - 去除所有可识别细节

3. **Secure Interaction Proxy** — 拦截 Agent 发出的所有操作指令，将占位符映射回原始值后在设备上执行。Agent 永远只操作匿名化界面。

4. **Privacy Gatekeeper** — 当推理需要对原始敏感值进行计算时（如比较两个手机号），在本地执行受限计算，仅返回非敏感结果给 Agent。

### 跨模态一致性

框架确保三个模态（用户指令、XML 层级、截图）的匿名化保持一致：
- 用户指令中的敏感词也被替换
- XML 中的敏感属性值被替换
- 截图中的敏感区域被遮盖/替换
- 使用会话作用域的本地映射表保证时间一致性

## 实验结果

在 **AndroidLab** 和 **PrivScreen** 两个基准上的实验结果：

- **隐私泄露大幅降低**：在多个模型（包括 GPT-4V、Claude 等）上，框架显著减少了 PII 泄漏率
- **效用损失有限**：任务完成率仅轻微下降，隐私-效用权衡达到当前最优
- **对比优势明显**：在 Table 1 的对比中，该框架是唯一同时满足"Agent 能使用敏感数据"和"Agent 看不到真实值"的方法

### 与现有方法的对比

| 方法 | 保护 PII | Agent 可用任务相关 PII | 跨模态一致 |
|------|---------|---------------------|-----------|
| CORE | ❌ 传输原始值 | ✅ | ❌ |
| DualTAP | ⚠️ 弱化保护 | ✅ | ❌ |
| PrivWeb | ❌ 授权后暴露 | ✅ | ❌ |
| GUIGuard | ✅ | ❌ 失去可用性 | ⚠️ |
| **本文** | ✅ | ✅ | ✅ |

## 关键洞察

1. **结构性隐私问题**：论文指出隐私泄露不是实现细节问题，而是当前移动 OS 生态的结构性属性——缺乏原生的、LLM 友好的交互协议（如 Tool Calling、MCP），导致 Agent 必须通过"看整个屏幕"来感知环境。

2. **确定性占位符是核心创新**：相比随机混淆或简单分类，类型保留 + 确定性映射让 Agent 能在匿名化界面上进行有意义的推理和操作。

3. **会话作用域映射表**解决了时间一致性问题：同一敏感值在多步交互中始终映射到同一占位符，避免 Agent 因占位符变化而产生 grounding 失败。

4. **长期方向**：论文认为根本解决方案需要移动 OS 原生支持语义化、隐私感知的 Agent 接口——这对手机端 AIOS 的系统设计有直接指导意义。

## 为什么重要

对手机端 AIOS 生态的意义：

- **安全底线**：随着 Agent 从"辅助"走向"自主操作"，隐私保护成为不可回避的系统级需求。该框架为 AIOS 的 Agent 安全层设计提供了可落地方案。
- **端云协同范式**：该工作展示了"敏感计算留在端侧、推理能力放在云端"的协作模式，是端云协同在安全领域的典型应用。
- **推动 OS 原生支持**：论文呼吁移动 OS 提供原生隐私感知接口，这对小米 HyperOS、华为 HarmonyOS 等系统的 Agent 框架设计有直接参考价值。
- **开源可用**：代码已开源（GitHub: one-step-beh1nd/gui_privacy_protection），可直接集成到现有 Agent 系统中。

## 关联

- [[gui-agent-privacy]] — GUI Agent 隐私保护的通用概念框架
- [[secagent-mobile-gui]] — SecAgent 的安全感知 GUI Agent 架构
- [[cora-mobile-gui-safety]] — CORA 的合规风险控制，互补安全维度
- [[turing-test-mobile-gui]] — 评估 GUI Agent 能力的基准，隐私是评估维度之一
- [[edge-cloud-offloading]] — 端云协同架构，隐私保护是卸载决策的关键约束
