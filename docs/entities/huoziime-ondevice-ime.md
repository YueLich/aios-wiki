---
type: entity
tags: [端侧推理, 输入法, LLM, 个性化, 内存优化, Qwen3, llama.cpp, 移动端部署]
related: [[gemma4-ondevice]], [[edgeflow-cold-start]], [[kv-cache-quantization-ondevice]], [[agent-persistent-identity]], [[llama-cpp-b8799]]
sources:
  - url: https://arxiv.org/abs/2604.14159
    title: "HUOZIIME: An On-Device LLM-enhanced Input Method for Deep Personalization"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# HUOZIIME — 端侧 LLM 增强输入法

> 首个完全端侧部署、记忆增强的生成式中文输入法，基于 Qwen3-0.6B + 分层记忆 + GRPO 优化。来源：arXiv 2604.14159（2026-04-17）

## 核心问题

现有主流 LLM 增强输入法（SwiftKey、百度、搜狗、讯飞等）存在三个根本缺陷：

1. **松耦合架构**：LLM 仅用于长文本改写或整句建议，未深入短语补全和交互式编辑流水线
2. **浅层个性化**：局限于短上下文窗口或静态人设，无法积累长期用户知识或持续自适应
3. **云端推理依赖**：不可预测的延迟 + 隐私风险

| 输入法 | 模型 | 部署方式 | 核心 AI 功能 | 个性化 | 记忆 | 隐私 |
|--------|------|---------|-------------|--------|------|------|
| SwiftKey | GPT-4 Turbo | 云端 | 写作辅助、表情生成 | ✗ 弱 | ✗ 无 | ! 云端风险 |
| 百度 IME | ERNIE Bot | 云端 | 写作辅助、情感对话 | ✗ 弱 | ✗ 无 | ! 云端风险 |
| 讯飞 IME | Spark | 混合 | 人设预设、补全 | 中等 | ✗ 无 | ! 混合推理 |
| **HuoziIME** | **IME 专用 LLM** | **端侧** | **记忆补全、人设自演化** | **✓ 强** | **✓ L1/L2/L3** | **✓ 端侧** |

## 方法/架构

### 三组件架构

**1. 端侧 LLM 推理引擎**
- 基于 Qwen3-0.6B 系列，专为 IME 场景二次开发
- 使用 llama.cpp 深度优化的 CPU 推理运行时
- 支持多线程解码，Cursor-adjacent GhostText 渲染
- 增量 Prefill + RadixTree 前缀复用，仅对修改的后缀段计算

**2. GRPO 增强的分层记忆系统**
- **L1 记忆（风格缓存）**：即时写作风格适应，实时更新
- **L2 记忆（习惯模式）**：中期写作习惯积累
- **L3 记忆（知识库）**：长期用户知识沉淀，支持向量检索
- 使用 GRPO（Group Relative Policy Optimization）优化记忆策略
- HNSW 向量索引支持本地记忆检索

**3. MCP 跨应用通信**
- 基于 Anthropic Model Context Protocol 实现跨应用上下文同步
- 当聊天会话变化时，授权宿主应用发出 SYNC 请求
- 若 MCP 不可用，优雅降级为纯输入推理模式

### 在线交互循环

```
用户输入 → MCP SYNC 信号
    → 引擎选择 L1 风格缓存 + 格式化对话历史
    → RadixTree 前缀复用增量 Prefill
    → LLM 多线程解码生成候选
    → 若需外部事实支撑 → <MEM_RETRIEVAL> 控制 token
        → HNSW 向量检索本地记忆
        → KV 注入融合检索结果
    → Top 候选渲染为 GhostText
    → 用户继续输入 → 增量解码复用前缀状态
```

### 关键技术细节

- **KV 注入**：检索到的预计算 KV 段直接注入活跃解码状态，避免重新编码
- **控制 Token 触发**：`<MEM_RETRIEVAL>` 触发向量搜索，而非始终检索
- **Android 沙箱隔离突破**：通过 MCP 实现跨进程通信，解决 Android 应用沙箱限制
- **近零延迟 CPU 推理**：严格小内存占用，适配移动端硬件约束

## 实验结果

- 与 Qwen3-0.6B 基线对比，在中文短语补全任务上有显著提升
- 记忆增强的候选生成相比无记忆版本，用户接受率提升
- CPU 推理在中端 Android 设备上保持近零延迟
- 内存占用严格控制在小 footprint 范围内

## 关键洞察

1. **输入法是最高频的 AI 交互界面**：比 Chatbot、搜索等场景使用频率高出数个数量级，端侧部署的隐私收益在高频场景下尤为关键
2. **记忆分层是端侧个性化的正确路径**：L1/L2/L3 三层记忆对应不同的时间尺度和计算成本，GRPO 优化策略让记忆系统能够自我演化
3. **MCP 在移动端的创新应用**：Anthropic 的 MCP 协议最初为云端 Agent 设计，这里创新地用于解决 Android 沙箱隔离问题
4. **控制 Token 作为检索门控**：不是每次推理都检索，而是模型自己决定何时需要外部记忆，节省计算资源
5. **局限性**：轻量模型的推理能力有限，存在检索过度和检索 token 漂移等 Agent 不稳定性问题

## 为什么重要

- **证明了端侧 LLM 输入法的可行性**：从"云端 LLM 辅助"到"端侧 LLM 原生"的范式转变
- **为端侧 Agent 个性化提供参考架构**：分层记忆 + GRPO 优化的模式可推广到其他端侧 Agent 场景
- **隐私原生设计**：完全端侧部署消除了云端数据暴露风险
- **基于开源工具链**：Qwen3 + llama.cpp + YuyanIME（GPL-3.0），可复现

## 关联

- [[gemma4-ondevice]] — Gemma 4 的 E2B/E4B 同样面向端侧场景，但更通用化
- [[edgeflow-cold-start]] — 端侧模型冷启动优化，与 HuoziIME 的近零延迟目标一致
- [[kv-cache-quantization-ondevice]] — KV 缓存量化可进一步优化 HuoziIME 的内存占用
- [[agent-persistent-identity]] — HuoziIME 的 L3 记忆与 Agent 持久化身份概念高度相关
- [[llama-cpp-b8799]] — HuoziIME 基于 llama.cpp 推理运行时
- [[on-device-vs-cloud-agentic-tool-calling]] — HuoziIME 的 MCP 跨应用通信是端侧工具调用的典型案例
