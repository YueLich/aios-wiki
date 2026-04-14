---
type: concept
tags: [agent, smartphone, system-design, mobile, native, gui-agent, agentic, runtime, EuroMLSys]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[gui-agent-privacy]], [[mga-memory-gui-agent]]
sources:
  - url: https://arxiv.org/abs/2602.22942v2
    title: "ClawMobile: Rethinking Smartphone-Native Agentic Systems (EuroMLSys 2026)"
    date: 2026-04-11
    reliability: high
  - url: https://github.com/ClawMobile/ClawMobile
    title: "ClawMobile 开源实现"
    date: 2026-04
    reliability: high
created: 2026-04-14
updated: 2026-04-14
---

# ClawMobile: 重新思考智能手机原生 Agent 系统

> EuroMLSys 2026 | 作者: Hongchao Du, Shangyu Wu 等 (MBZUAI / CityU HK) | 开源: https://github.com/ClawMobile/ClawMobile

## 核心问题

手机端 Agent 面临独特挑战——受限执行上下文、碎片化控制接口、快速变化的应用状态。

现有方法的矛盾：UI 交互覆盖面广但对 UI 漂移和时序敏感；Tool/API 控制更稳定但跨 App 能力不足。**真实世界移动 Agent 失败往往因为执行被设备多变条件打断，而非规划能力不足。**

## 系统架构

分层架构，显式分离高层语言推理与底层设备执行。三大组件：

### Agent Orchestrator（编排器）
- 顶层推理循环：将用户输入转化为可执行计划
- **不直接操作界面**，通过工具调用与 Control Backends 交互
- 每次执行后重新查询设备状态验证进度

### Control Backends（控制后端）

| 后端类型 | 特点 | 适用 |
|---------|------|------|
| **确定性** (ADB, Termux API) | 语义确定，成本低 | 优先使用 |
| **UI Agent** | 语义理解屏幕，灵活但不确定 | 确定性路径不足时 |
| **直接 UI 控制** | 底层操作，覆盖广但语义弱 | 兜底 |

原则：**确定性优先**——先结构化控制，再概率性 UI 推理。

### Memory（记忆）
- 提供移动端知识、执行偏好，影响后端选择
- 与任一后端解耦

## 执行感知调度

调度是**迭代过程**：
1. Orchestrator 生成计划 → 查询 Memory 确认 API
2. 确定性后端 → UI Agent → 直接 UI 控制（依次升级）
3. 执行后验证设备状态
4. 未完成 → 重新规划，继续循环

关键创新：**每个调用有明确预期结果，执行后重查设备状态验证**。

## 实验结果

Google Pixel 9 (Android 16)，GPT-5.2，对比 DroidRun (DR)：

| App | 任务 | 完成率 DR/CM | 耗时/s DR/CM |
|-----|------|-------------|-------------|
| Settings | 暗色主题 | 100/**100** | 26/**21** |
| Chrome | 搜索金价 | 73/**100** | 26/**67** |
| Play | 安装小红书 | 33/**100** | 29/**117** |
| YouTube | 播放MV跳广告 | 100/**100** | 66/**88** |
| YouTube | MV评论留言 | 85/**100** | 121/**235** |
| 跨App | 搜英超写摘要 | 73/**100** | 60/**145** |

ClawMobile **6/6 任务 100% 完成**，DroidRun 在复杂任务失败。代价是平均慢 57.5 秒。

### 失败案例分析

DroidRun 跨 App 搜索的 3 种失败：
1. **异步启动** — Chrome 启动慢，误判失败
2. **歧义 UI** — 点搜索框误触历史记录
3. **错误成功检测** — Notes 未创建笔记就判定完成

ClawMobile 缓解：每次操作后重查状态、检测启动中等待、失败时重新评估选替代后端。

## 三大研究挑战

### ⚡ 效率
- 高效状态表示（增量更新替代全量序列化）
- 混合调度（确定性 vs 概率性的成本 × 可靠性）
- 模型部署（云端延迟 vs 端侧硬件限制 → 混合策略）

### 🔄 适应性
- 技能抽象（从轨迹提取可复用技能）
- 分层记忆（短期上下文 vs 长期技能）
- 领域专业化

### 🛡️ 稳定性
- 显式进度验证 + 容错恢复
- 隐私保护（有界日志、权限仲裁）

## 为什么重要

将移动 Agent 视为**运行时系统问题**而非算法问题。与 [[apple-intelligence]] App Intents、小米 HyperAI 系统级集成思路一致——Agent 不应是外挂，应是 OS 一部分。

## 关联

- [[secagent-mobile-gui]] — 语义增强 GUI Agent
- [[mga-memory-gui-agent]] — 记忆驱动（解决适应性 RQ2）
- [[pspa-bench-gui-agent]] — 个性化评估
- [[gui-agent-privacy]] — 隐私保护（解决稳定性 RQ3）
- [[turing-test-mobile-gui]] — 拟人化基准
- [[edgeflow-cold-start]] — 冷启动（解决效率 RQ1）
