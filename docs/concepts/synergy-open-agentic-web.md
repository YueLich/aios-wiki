---
type: concept
tags: [agent, open-agentic-web, lifelong-learning, identity, collaboration, multi-agent]
related: [[agent-persistent-identity]], [[exectune-guide-core-policy]], [[clawmobile-agentic]], [[emommas-edge-negotiation]], [[mga-memory-gui-agent]], [[mobiflow-benchmark]]
sources:
  - url: https://arxiv.org/abs/2603.28428
    title: "Synergy: A Next-Generation General-Purpose Agent for Open Agentic Web"
    date: 2026-03-28
    reliability: high
created: 2026-04-16
updated: 2026-04-16
---

# Synergy：开放代理网络的下一代通用 Agent

> 论文提出"Agentic Citizen"概念——Agent 不再是工具调用的封装，而是能在开放网络中协作、拥有持久身份、持续进化的数字公民。来自 arXiv 2603.28428。

## 核心问题

当前 AI Agent 存在三大结构性缺陷：

1. **封闭沙箱式协作**：即使是"多 Agent"系统（如 AdaptOrch、Symphony、OpenClaw），也只是在集中控制下调度内部子 Agent，无法作为对等参与者加入开放网络。Agent 之间存在系统性过度自信、沟通冗长、指令遵循不稳定等行为缺陷。

2. **无身份的工具化**：每次交互从零开始，Agent 无法积累声誉、建立用户关系、形成行为一致性。用户已经在发展"身份保护策略"来应对平台身份丢失（Lee et al., 2026），但当前架构没有持久身份机制。

3. **静态部署后的停滞**：记忆增强架构（Agentic Memory、HiMem）只在单一维度（任务完成率）上优化。Agent 在 100 次会话中代码生成准确率提高，但沟通能力毫无进步——这不是真正的"进化"。

## 方法/架构

Synergy 定义了 **Agentic Citizen（AC）**的形式化框架：

AC(a, W) ⟺ C(a, W) ∧ I(a) ∧ E(a)

三个条件缺一不可：

### 1. 开放网络原生协作（C）

- **持久联系人 + 跨会话消息传递**：Agent 可以维护"通讯录"，跨会话边界交换消息
- **Agora 工作空间**：基于仓库的协作表面，Agent 可以共享代码、文件、执行上下文
- **委托会话 + 远程环境扩展**：任务可以分支到后台子任务，通过 mailbox 机制异步传递结果
- **关键区分**：不是消息传递，而是"在持久工件、历史记录和执行上下文上的共享工作"——分支、修改、交接、重新整合结果，且全程保持委托责任链

### 2. Agent 身份与人格（I）

- **类型化长期记忆**：不只是事实存储，而是笔记、档案、技能、议程、社交关系的综合体
- **隐藏维护例程**：Agent 在后台持续整理自身状态
- **"生活世界"积累**：Agent 不仅记住事实，还积累一个完整的"生活世界"（lifeworld）

### 3. 终身进化（E）

- **经验中心学习机制**：将交互轨迹编码为结构化经验记录（推断意图 + 蒸馏执行脚本 + 源模型元数据 + 检索到的先验经验链接）
- **多维奖励推断**：当显式奖励不可用时，通过专用奖励 Agent 评估短期交互窗口推断奖励
- **自适应回忆**：推理时自适应回忆高价值经验

### 系统架构

- **作用域附加无状态服务器**：服务器不绑定单个项目/交互 shell/机器网关，客户端以作用域（通常来自工作目录）连接运行时
- **会话作为主要执行胶囊**：prompting、工具使用、规划状态、摘要、本地连续性和交付都在会话内组装
- **父子会话 + mailbox 异步组合**：后台任务分支、跨会话交付通过 mailbox 机制（而非隐式共享上下文）
- **Cortex 管理子会话**：复杂任务在主会话启动，通过 Cortex 管理子会话分支

## 实验结果

### 能力随经验积累增长

| 基准 | 模型 | 轮次 | 起始 | 最佳 | 提升 (pp) | 相对提升 | 第5轮已完成 |
|------|------|------|------|------|-----------|----------|-------------|
| SWE-bench Verified | Qwen 3.5 397B A17B | 15 | 63.0% | 82.6% | +19.6 | +31.1% | 71.4% |
| SWE-bench Verified | Nex 1.1 | 12 | 60.8% | 83.0% | +22.2 | +36.5% | 72.1% |
| OpenRCA | Qwen 3.5 397B A17B | 8 | 11.94% | 29.6% | +17.7 | +148.1% | 72.7% |

关键发现：
- 增长曲线**单调递增**，不是围绕基线的噪声波动
- 跨两个模型家族（Qwen、Nex）和两个任务域（软件工程、运维诊断）均成立
- 经验捕获高效——第 5 轮已实现 70%+ 的最终改进
- SWE-bench 平均补丁生成率保持 ~95%，说明增长过程操作稳定

### 经验可迁移性（OneMillion Benchmark）

| 指标 | 无经验基线 | 注入经验 | 变化 |
|------|-----------|----------|------|
| 平均分 | 20.64 | 48.44 | +27.8 pp |
| 中位数 | 17.86 | 50.58 | +32.7 pp |
| 通过率 | 3.79% | 23.51% | +19.7 pp |
| 负分率 | 21.28% | 3.78% | -17.5 pp |

跨域提升（每个 OneMillion 领域都改善）：
- 医疗：27.72 → 60.37 (+32.7 pp)
- 经济金融：14.49 → 44.84 (+30.4 pp)
- 自然科学：19.00 → 46.66 (+27.7 pp)
- 工业：22.86 → 49.09 (+26.2 pp)
- 法律：17.98 → 40.10 (+22.1 pp)

**负分率从 21.28% 降至 3.78%**——这是质变：Agent 从"经常帮倒忙"变成"几乎从不帮倒忙"，代表了操作可靠性的根本性改变。

## 关键洞察

1. **经验是可移植的能力资产**：不是私有优化，而是可以打包交给新 Agent 实例的"能力包"。新 Agent 接收后立即获得更强的起始性能。

2. **经验捕获的是通用策略而非领域捷径**：五个差异巨大的领域都受益，说明编码的是任务分解、工具使用、错误恢复等可迁移模式。

3. **Agentic Citizen 概念对端侧 Agent 的启示**：手机端 Agent 也需要持久身份（记住用户偏好）、终身进化（从交互中学习）、开放协作（跨设备、跨 App 协作）。Synergy 的架构虽然面向云端，但其三个条件（协作/身份/进化）可以直接迁移到端侧设计。

4. **从工具到数字公民的范式转变**：论文引用了"Agent 正在成为互联网的新实体，继移动 App 之后"这一判断。对手机端 AIOS 来说，这意味着 Agent 不应只是 App 内的功能，而应是跨 App 的持久存在。

## 关联

- [[agent-persistent-identity]] — Synergy 的身份系统与多锚点持久身份架构的对比
- [[exectune-guide-core-policy]] — Guide Model 引导 vs Synergy 经验学习
- [[clawmobile-agentic]] — 原生 Agent 系统 vs 开放网络 Agent
- [[emommas-edge-negotiation]] — 多 Agent 协商 vs Synergy 的开放网络协作
- [[mga-memory-gui-agent]] — 记忆驱动 GUI Agent 的记忆机制 vs Synergy 的终身记忆
- [[mobiflow-benchmark]] — 移动 Agent 基准测试 vs Synergy 的 OneMillion Benchmark
