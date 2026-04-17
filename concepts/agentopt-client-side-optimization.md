---
type: concept
tags: [agent, optimization, client-side, model-selection, budget-allocation, LangGraph]
related: [[clawmobile-agentic]], [[exectune-guide-core-policy]], [[edge-cloud-offloading]], [[agent-persistent-identity]], [[comllm-mec-offloading]], [[edgeflow-cold-start]]
sources:
  - url: https://arxiv.org/abs/2604.06296
    title: "AgentOpt v0.1 Technical Report: Client-Side Optimization for LLM-Based Agent"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# AgentOpt v0.1: 客户端 Agent 优化框架

> 首个系统性研究 Agent 客户端优化的技术报告，将模型选择和预算分配建模为组合搜索问题，在 4 个基准测试上验证了比暴力搜索高 10-40x 效率提升。

## 核心问题

当前 AI Agent 优化研究几乎全部聚焦**服务端**——请求调度、负载均衡、推测执行、缓存复用等。但随着用户越来越多地自行编排 Agent 工作流（组合本地工具、远程 API、多种模型），**客户端**同样存在大量关键优化决策：

- 每个工作流角色应该分配哪个模型？
- API 预算如何在多步骤间分配？
- 何时调用本地工具 vs 云端模型？
- 质量-成本-延迟权衡如何取舍？

这些决策高度依赖应用场景，无法由模型提供商从服务端统一优化。一个创业公司可能接受小幅精度下降换取大幅成本削减，而医疗决策系统则必须优先保障可靠性。

## 方法/架构

AgentOpt 将客户端优化建模为**组合搜索问题**：

### 问题形式化
- 每个 Agent 工作流有 K 个角色（planner、solver、answerer、critic 等）
- 每个角色可从 M 个候选模型中选择
- 总搜索空间 = M^K 种组合
- 目标：在固定评估预算下找到最优模型组合

### 搜索算法
论文比较了多种搜索策略：
- **暴力搜索 (Brute Force)**：穷举所有组合——准确但昂贵
- **随机搜索 (Random)**：随机采样组合
- **Greedy**：逐角色贪心选择
- **Matrix UCB-E**：基于多臂老虎机的探索策略，**表现最优**

Matrix UCB-E 将每个模型组合视为一个 arm，利用 UCB 策略在探索和利用之间平衡，在较大组合空间上一致性地优于其他方法。

### 关键设计
- AgentOpt 通过 **httpx 传输层拦截**所有 LLM 请求，用 Python contextvars 应用模型覆盖
- **无需修改 Agent 代码**——可与任何 LangGraph/AutoGen 工作流集成
- 支持异步并行评估多个组合

## 实验结果

### 基准测试设置
| 基准 | 任务 | 管道结构 | 组合数 |
|------|------|----------|--------|
| HotpotQA | 多跳问答 | planner + solver | 81 |
| GPQA Diamond | 研究生科学 | 单模型 | 9 |
| MathQA | 数学推理 | answerer + critic | 81 |
| BFCL v3 | 函数调用 | 单模型 | 9 |

评估了 9 个模型：Claude Opus 4.6、Claude Haiku 4.5、Claude 3 Haiku、gpt-oss-120b/20b、Kimi K2.5、Qwen3 Next 80B、Qwen3 32B、Ministral 3 8B。

### 关键发现

**最优组合不等于最强模型**：
- HotpotQA 最优：Ministral 3 8B (planner) + Claude Opus 4.6 (solver) = 74.27%
- 而 Claude Opus 4.6 + Claude Haiku 4.5 反而只有 31.77%
- **最强模型作为 planner + 弱模型作为 solver 时反而表现差**——说明模型必须在工作流上下文中评估

**Matrix UCB-E 效率**：
- 在 81 组合空间中，Matrix UCB-E 以远少于暴力搜索的评估次数达到接近最优精度
- 暴力搜索 HotpotQA 需要 $51.90，而 Matrix UCB-E 大幅降低评估成本

**模型质量是上下文相关的**：
- Claude Opus 4.6 在 BFCL 上与 Qwen3 Next 80B 并列最优，但后者便宜 32 倍
- 不同工作流角色对模型能力的需求完全不同

## 关键洞察

1. **客户端 vs 服务端优化是正交的**：服务端优化关注吞吐和利用率，客户端优化关注应用特定效用——两者必须协同
2. **组合爆炸是真实问题**：即使 2 个角色 × 9 个模型 = 81 种组合，暴力搜索成本已不可接受（$52-$124）
3. **Agent 系统设计需要成本意识**：客户端优化使开发者能够显式控制质量-成本权衡，这对移动端 Agent 尤为重要（端侧小模型 + 云端大模型的混合策略）
4. **可扩展性强**：论文指出框架可扩展到自适应路由、工具选择、调度和个性化策略

## 为什么重要

对手机端 AIOS 生态而言，AgentOpt 直接解决了端云协同中的核心难题：

- **端侧 Agent 模型选择**：在手机上运行 Agent 时，需要在端侧小模型（低延迟、零成本）和云端大模型（高精度）之间动态切换
- **预算感知调度**：移动端用户的 API 预算有限，AgentOpt 的组合优化框架天然适用于移动端的成本约束场景
- **与 AIOS 架构互补**：[[clawmobile-agentic]] 定义了原生 Agent 系统架构，AgentOpt 提供了该架构下的资源优化方法论
- **客户端拦截设计**：通过 httpx 传输层拦截实现透明优化，不侵入 Agent 代码——这对移动端 SDK 集成至关重要

## 关联

- [[clawmobile-agentic]] — AgentOpt 的客户端优化可直接应用于 ClawMobile 的多角色管道
- [[exectune-guide-core-policy]] — AgentOpt 的模型选择策略可与 ExecTune 的引导策略协同
- [[edge-cloud-offloading]] — AgentOpt 提供了端云模型选择的理论框架
- [[comllm-mec-offloading]] — 互补：COMLLM 处理计算卸载，AgentOpt 处理模型选择
- [[edgeflow-cold-start]] — 冷启动场景下端侧模型的快速选择
- [[agent-persistent-identity]] — Agent 身份与模型选择的一致性问题
