---
type: concept
tags: [gui-agent, benchmark, mobile-agent, failure-analysis, android, screentext, screenshot, multimodal]
related: [[pspa-bench-gui-agent]], [[mga-memory-gui-agent]], [[clawmobile-agentic]], [[agent-persistent-identity]], [[mobiflow-benchmark]]
sources:
  - url: https://arxiv.org/abs/2604.17817
    title: "Do LLMs Need to See Everything? A Benchmark and Study of Failures in LLM-driven Smartphone Automation using Screentext vs. Screenshots"
    date: 2026-04-20
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# DailyDroid: 移动 Agent 失败分析基准

> 75 个日常任务的系统性失败分析 — 揭示 LLM 驱动手机自动化的核心瓶颈（arXiv 2604.17817, 2026-04-20）

## 核心问题

LLM 驱动的移动 Agent（如 AppAgent、MobileAgent）在手机自动化上表现不佳——低准确率、误读用户意图、复杂任务提前终止——但此前缺乏系统性的"为什么失败、在哪里失败"的诊断研究。现有基准（MobileAgentBench、A3、AndroidWorld）多关注任务成功率数字，缺少对失败模式的深入分类和可复现的失败追踪。

## 方法/架构

### DailyDroid 基准

- **75 个任务**，覆盖 **25 款 Android 应用**，分 **5 个场景**（通讯、效率、媒体、社交、工具）
- **3 个难度等级**（简单/中等/困难），模拟真实日常手机使用
- **300 次试验**（2 模型 × 2 模态 × 75 任务）

### 评估设计

**模型**: GPT-4o（基线） vs o4-mini（推理增强型）

**输入模态对比**:
- **Text-only（纯文本）**: 仅使用 Android UI 树（screentext）——结构化 HTML-like 表示
- **Multimodal（多模态）**: 文本 + 截图（screenshot）——模拟当前主流 Agent 的工作方式

### Agent 系统架构（四模块）

| 模块 | 功能 | 关键实现 |
|------|------|----------|
| **感知（Perception）** | 捕获手机环境状态 | UI 树解析 + 截图 |
| **规划（Planning）** | 基于 LLM 推理制定行动策略 | 提示工程 + 反思/回溯 |
| **执行（Action）** | 将高层指令映射为设备操作 | Android UI Automator + ADB |
| **记忆（Memory）** | 保留历史交互信息 | 短期: prompt 注入; 长期: 预训练知识 |

## 实验结果（关键数据）

### 失败分类体系

研究提出了**双层失败手册**（Failure Handbook），将失败分为：

**系统级失败**（基础设施崩溃，强制终止）:
| 子类 | 描述 | GPT-4o 文本 | GPT-4o 多模态 | o4-mini 文本 | o4-mini 多模态 |
|------|------|------------|-------------|------------|--------------|
| UI 获取失败 | 无法抓取完整应用 UI | 25 (33.3%) | 25 (33.3%) | 23 (30.7%) | 23 (30.7%) |
| UI 解析失败 | 抓取到但无法解析所需组件 | 3 (4.0%) | 3 (4.0%) | 4 (5.3%) | 5 (6.7%) |
| UI 逻辑异常 | UI 设计歧义/反直觉 | 1 (1.3%) | 1 (1.3%) | 0 | 0 |
| 执行失败 | 识别正确但无法执行 | 3 (4.0%) | 3 (4.0%) | 3 (4.0%) | 2 (2.7%) |
| **系统级合计** | | **32 (42.7%)** | **32 (42.7%)** | **30 (40.0%)** | **30 (40.0%)** |

**Agent 级失败**（系统正常但 Agent 出错）:
| 子类 | 描述 | GPT-4o 文本 | GPT-4o 多模态 | o4-mini 文本 | o4-mini 多模态 |
|------|------|------------|-------------|------------|--------------|
| LLM 预测错误 | 理解屏幕但做出错误判断 | 10 (13.3%) | 7 (10.8%) | 7 (9.3%) | 3 (4.0%) |
| LLM 反思失败 | 无法识别任务完成或步骤错误 | 2 (2.7%) | 1 (1.3%) | 2 (2.7%) | 2 (2.7%) |
| 超出步数限制 | 因低效/循环超过最大步数 | 0 | 1 (1.3%) | 3 (4.0%) | 7 (9.3%) |
| **Agent 级合计** | | **23 (30.7%)** | **19 (25.3%)** | **23 (30.7%)** | **20 (26.7%)** |

### 核心发现

1. **UI 感知是最大瓶颈**: 系统级 UI 获取失败占比最高（~33%），且不受模态影响——无论文本还是截图，都无法解决 UI 组件缺失问题
2. **多模态提升有限但关键**: 多模态输入仅"边际提升"成功率，但在 LLM 预测错误方面显著改善（GPT-4o: 13.3% → 10.8%, o4-mini: 9.3% → 4.0%）
3. **o4-mini 推理能力更强但更慢**: 推理增强模型减少了 LLM 预测错误，但增加了步数超限（因为更谨慎的探索策略）
4. **应用生态问题是根本**: 很多失败源于 App 本身的 UI 无障碍缺陷（缺失按钮标签、无替代文本），不是 Agent 设计问题

## 关键洞察

**UI 无障碍 = Agent 感知**: 这篇论文揭示了一个深层关联——移动 Agent 面临的感知难题与视障用户的 UI 无障碍问题是同一枚硬币的两面。App 开发者如果改善 UI 标签和无障碍特性，同时也在帮助 AI Agent 更好地操作。

**"知道该做什么但做不到"**: 在多个失败案例中，截图提供了足够的视觉上下文让 LLM 正确识别下一步操作，但由于目标 UI 元素在解析后的文本表示中缺失，Agent 无法执行。这种"感知-执行鸿沟"是当前 GUI Agent 的核心痛点。

**基准设计启示**: DailyDroid 选择了 25 款主流第三方应用（非 Google 精选应用），更贴近真实使用场景，暴露了"野生"应用中的 UI 解析泛化问题。

## 为什么重要

对手机端 AI 生态的意义：
- **端侧 Agent 设计指导**: 明确了端侧 GUI Agent 的改进方向——UI 解析鲁棒性比多模态融合更紧迫
- **系统级 vs Agent 级失败分离**: 帮助开发者区分"基础设施问题"和"AI 能力问题"，避免无效优化
- **App 生态协同**: 呼吁 Android/iOS 平台加强 UI 无障碍标准，这将同时惠及人类用户和 AI Agent
- **输入模态选择**: 对于资源受限的端侧场景，纯文本（UI 树）输入可能是比截图更高效的选择，且性能差距不大

## 关联

- [[pspa-bench-gui-agent]] — 另一个 GUI Agent 基准，关注屏幕理解
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent，可能从 DailyDroid 的失败分类中获益
- [[clawmobile-agentic]] — 原生 Agent 系统架构，与 DailyDroid 的四模块模型互补
- [[agent-persistent-identity]] — Agent 持久化身份，可减少"反思失败"类错误
- [[mobiflow-benchmark]] — 移动 Agent 基准，与 DailyDroid 形成方法论对比
