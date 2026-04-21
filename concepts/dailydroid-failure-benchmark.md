---
type: concept
tags: [gui-agent, benchmark, failure-analysis, mobile-agent, android, perception, multimodal]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[clawmobile-agentic]], [[mga-memory-gui-agent]], [[mobiflow-benchmark]]
sources:
  - url: https://arxiv.org/abs/2604.17817
    title: "Do LLMs Need to See Everything? A Benchmark and Study of Failures in LLM-driven Mobile GUI Agents"
    date: 2026-04-21
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# DailyDroid: Mobile GUI Agent 失败分析基准

> 一个包含 75 个任务、覆盖 25 个 Android 应用的移动 Agent 失败分析基准，系统性揭示了 LLM 驱动的手机 GUI Agent 的失败模式与根因。

## 核心问题

当前 LLM 驱动的移动 Agent（如基于 GPT-4o、Claude 等的 GUI 自动化系统）在日常手机任务中表现不佳，但学术界缺乏系统性的失败分析。现有基准（MobileAgentBench、A3、AndroidWorld）主要关注任务成功率，很少深入研究"Agent 在哪里以及为什么失败"。

## 方法/架构

### DailyDroid 基准设计

- **75 个任务**，覆盖 **25 个主流第三方 Android 应用**
- **5 个场景类别**：生产力工具、系统工具、信息获取、媒体娱乐、社交通信
- **3 个难度等级**：Simple / Medium / Hard（每应用 3 个任务）
- 任务设计贴近真实日常使用（如日历创建事件、Spotify 播放音乐、Chrome 搜索信息）

### 失败分类体系（Failure Handbook）

论文提出了一个两层失败分类框架：

**系统级失败（System-Level）**：发生在感知模块，Agent 无法正确获取或解析 UI 信息。
- **UI 检索失败**（UI Retrieval）：无法获取完整应用 UI — GPT-4o: 33.3%, o4-mini: 30.7%
- **UI 解析失败**（UI Parsing）：获取了 UI 但无法识别所需组件 — 4.0%~6.7%
- **UI 逻辑问题**（UI Logic）：UI 设计歧义或反直觉 — 1.3%
- **执行失败**（Execution）：识别正确但执行出错 — 2.7%~4.0%

**Agent 级失败（Agent-Level）**：发生在推理模块，Agent 能感知 UI 但决策错误。
- **LLM 预测错误**（LLM Prediction）：理解屏幕内容但做出错误决策 — GPT-4o: 13.3%, o4-mini: 4.0%（多模态）
- **LLM 反思失败**（LLM Reflection）：无法识别任务完成或步骤错误 — 1.3%~2.7%
- **步数超限**（Reaching Max Step）：因低效循环或正确但过慢的路径而超步 — o4-mini 多模态: 9.3%
- **不可能任务**（Impossible Task）：因任务设计意图或歧义无法完成 — 1.3%

## 实验结果/关键数据

### GPT-4o vs o4-mini 失败率对比

| 模式 | GPT-4o 系统级 | GPT-4o Agent级 | o4-mini 系统级 | o4-mini Agent级 |
|------|-------------|--------------|--------------|--------------|
| Text-only | 42.7% | 30.7% | 40.0% | 30.7% |
| Multimodal | 42.7% | 25.3% | 40.0% | 26.7% |

### 关键发现

1. **系统级失败是主要瓶颈**：UI 检索失败占所有失败的 ~33%，是最大的单一失败原因。如果 Agent 无法正确感知 UI，后续推理完全无效。
2. **多模态并未显著改善系统级失败**：添加截图后系统级失败率不变（42.7%→42.7%），仅 Agent 级失败略有下降。
3. **UI 可访问性是根本问题**：失败根因常在于屏幕表示中缺失文本内容——即使截图提供了足够的视觉信息让 LLM 识别正确操作步骤，目标 UI 元素仍然缺失。
4. **o4-mini 在多模态下步数超限更多**：o4-mini 多模态的 Reaching Max Step 率达 9.3%（vs text-only 4.0%），说明较小模型在处理视觉信息时效率更低。

## 关键洞察

**"看得到但做不到"悖论**：论文最深刻的发现是，多模态 Agent 经常出现"screenshot 提供了足够信息让 LLM 知道该做什么，但 task 仍然失败"的情况。这是因为 UI 元素在解析后的数据表示中缺失，即使视觉上是可见的。这揭示了从像素到可操作语义之间的巨大鸿沟。

**系统级 vs Agent 级失败的比例关系**：系统级失败（42.7%）远超 Agent 级失败（25-31%），说明当前移动 Agent 的主要瓶颈不在 LLM 推理能力，而在 UI 感知和解析能力。这对端侧部署有重要启示——与其追求更大的模型，不如投资更好的 UI 解析管线。

**与 W3C 无障碍指南的关联**：论文指出 App 开发者未遵循无障碍标准（如缺失按钮标签、图片缺替代文本）是 Agent 失败的深层原因。这意味着移动 Agent 的进步不仅依赖 AI 技术，还需要整个 App 生态的可访问性改善。

## 为什么重要

1. **基准设计范式转变**：从"测成功率"转向"分析失败原因"，为移动 Agent 研究提供新视角
2. **端侧 Agent 部署的指导**：明确了 UI 感知是比模型能力更关键的瓶颈
3. **失败手册（Failure Handbook）**：可复用的诊断工具，帮助开发者系统排查 Agent 失败
4. **多模态效果的实证**：首次系统量化了截图对移动 Agent 的实际影响，结论出人意料

## 关联
- [[secagent-mobile-gui]] — GUI Agent 安全与感知
- [[pspa-bench-gui-agent]] — GUI Agent 规划基准
- [[clawmobile-agentic]] — 原生移动 Agent 架构
- [[mga-memory-gui-agent]] — 记忆驱动的 GUI Agent
- [[mobiflow-benchmark]] — 移动 Agent 工作流基准
- [[gui-agent-privacy]] — GUI Agent 隐私保护
