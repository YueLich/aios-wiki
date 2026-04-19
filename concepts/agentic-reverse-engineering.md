---
type: concept
tags: [Agent安全, 逆向工程, LLM Agent, 二进制分析, 安全研究, agentic系统]
related: [[secagent-mobile-gui]], [[clawmobile-agentic]], [[agent-persistent-identity]]
sources:
  - url: https://arxiv.org/abs/2604.14317
    title: "Challenges and Future Directions in Agentic Reverse Engineering Systems"
    date: 2026-04-15
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# Agentic 逆向工程系统

> Salem Radey, Jack West, Kassem Fawaz — 系统性分析 LLM Agent 在二进制逆向工程中的能力边界与未来方向。arXiv:2604.14317。

## 核心问题

基于 LLM 的 Agent 系统正被用于复杂安全任务，包括二进制逆向工程（RE）。但这些系统在真实场景中仍面临严重限制——涉及混淆、时序分析和特殊架构的复杂 RE 场景中，前沿系统仍会失败。

## 三种分析方法

| 方法 | 描述 | Agent 表现 |
|------|------|-----------|
| 静态分析 | 不运行程序，仅分析编译代码 | 基本功能识别可完成，但复杂混淆场景失败 |
| 动态分析 | 运行程序并观察行为 | 运行时交互能力有限，时序敏感场景困难 |
| 混合分析 | 结合静态和动态 | 理论最优，但 Agent 协调复杂度高 |

## 关键限制

1. **Token 约束**：大型二进制文件的分析需要处理海量 token，超出上下文窗口限制
2. **混淆处理困难**：代码混淆（control flow flattening、opaque predicates）严重降低 Agent 的分析准确率
3. **缺乏程序护栏**：当前 Agent 系统缺少足够的安全约束，可能执行危险操作（如运行恶意代码）
4. **工具使用局限**：Agent 对逆向工具（Ghidra、IDA Pro）的调用能力有限，复杂交互场景失败率高

## 未来方向（研究者视角）

- **分层 Agent 架构**：将 RE 任务分解为多个专业化 Agent（静态分析 Agent、动态测试 Agent、结果整合 Agent）
- **程序语义理解增强**：超越 token 级别的代码理解，建立程序语义级别的推理能力
- **安全沙箱集成**：将 Agent 操作限制在安全环境中，防止意外执行恶意行为
- **跨架构支持**：扩展 Agent 对 ARM、RISC-V 等移动端常见架构的分析能力

## 对手机端 AIOS 的意义

Agent 系统的安全能力直接影响移动设备的安全防护水平：
- 端侧 Agent 能否分析 APK/ELF 二进制检测恶意代码？
- 移动设备的 NPU 能否加速 Agent 驱动的实时安全分析？
- 端侧 Agent 的安全约束（防注入、防越权）是移动安全的核心课题

当前的 token 约束和混淆处理问题，对端侧部署尤其严峻——移动设备的内存和算力远低于云端服务器。

## 关联

- [[secagent-mobile-gui]] — 移动 GUI Agent 的安全感知机制
- [[clawmobile-agentic]] — 原生 Agent 系统的架构设计
- [[agent-persistent-identity]] — Agent 持久化身份在安全场景的需求
- [[gui-agent-privacy]] — Agent 系统的隐私保护机制
- [[ggml-llamacpp-hf]] — 端侧推理框架是安全分析 Agent 的基础设施
