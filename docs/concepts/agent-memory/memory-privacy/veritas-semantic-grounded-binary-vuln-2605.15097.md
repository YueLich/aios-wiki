---
title: "Veritas: A Semantically Grounded Agentic Framework for Memory Corruption Vulnerability Detection in Binaries"
arXiv: 2605.15097
date: 2026-05-14
tags: [agent-memory, memory-privacy, security, binary-analysis]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

检测剥离二进制文件中的内存崩溃漏洞需要从低层次、有损的表示中恢复对象语义、过程间传播和可行触发器。近期基于 LLM 的方法改善了代码理解，但可靠检测仍需要建立在内存相关语义和运行时可行性证据的基础上。Veritas 提出了一个语义 grounded 的二进制内存崩溃漏洞检测框架，将 RetDec 提升的 LLVM IR 上的静态切片器、双视角 LLM 检测器（使用反编译 C 和选择性 LLVM IR 对 grounded 流程进行逐步推理）以及多 Agent 验证器（通过引导调试、断点检查和内存检查预言机来验证假设）相结合。切片器从 LLVM IR 事实（包括 def-use、调用、返回、全局变量和指针操作）重建值流关系，并发出紧凑的 witness-backed 流对象。检测器利用这些 artifacts 来推理控制流、边界和对象对应关系，而无需重新发现整个二进制的传播。验证器通过引导调试、断点检查和内存检查预言机确认或拒绝候选项。Veritas 在真实二进制漏洞案例的精选基准上实现了 90% 的召回率。在假阳性评估中，对 623 个检测器候选项进行了穷举验证和人工审核，穷举子集无假阳性，额外审核识别出两个确认的假阳性。在实际应用中，Veritas 发现了一个之前未知的 Apple 漏洞，已确认并分配了 CVE。

## 核心贡献

1. **语义 grounding 设计原则**：将语义 grounding 作为实用二进制漏洞检测的操作设计原则。
2. **RetDec-lifted LLVM IR 静态切片器**：重建值流关系，发出紧凑的 witness-backed 流对象。
3. **双视角 LLM 检测器**：使用反编译 C 和选择性 LLVM IR 对 grounded 流程进行逐步推理。
4. **多 Agent 验证器**：通过引导调试、断点检查和内存检查预言机验证假设。
5. **发现真实漏洞**：在实际应用中发现并确认了 Apple 漏洞（已分配 CVE）。

## 为什么重要

二进制安全分析是 Agent 记忆系统在安全领域的重要应用。Veritas 展示了如何将 LLM Agent 与结构化内存（LLVM IR 值流）结合，实现可靠的漏洞检测。该工作对安全 Agents 的记忆系统设计具有重要参考价值。

## 与移动端/端侧的相关性

移动端安全检测 Agents 需要分析应用二进制文件，Veritas 的语义 grounded 方法对端侧安全分析具有参考价值。框架的模块化设计也适合在资源受限环境中部署。
