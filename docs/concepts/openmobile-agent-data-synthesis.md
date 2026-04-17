---
type: concept
tags: [mobile-agent, data-synthesis, gui-agent, vlm, android, open-source, 任务合成, 轨迹合成]
related: [[clawmobile-agentic]], [[pspa-bench-gui-agent]], [[secagent-mobile-gui]], [[mga-memory-gui-agent]], [[mobiflow-benchmark]], [[exectune-guide-core-policy]]
sources:
  - url: https://arxiv.org/abs/2604.15093
    title: "OpenMobile: Building Open Mobile Agents with Task and Trajectory Synthesis"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# OpenMobile: 开放移动 Agent 数据合成框架

> 解决闭源移动 Agent 与开源社区之间性能鸿沟的开放数据合成框架，在 AndroidWorld 上将开源模型从 ~30% 提升到 64.7%。

## 核心问题

移动 Agent 领域存在严重的"数据不透明"问题：Step-GUI、MAI-UI、UI-Venus-1.5、MobileAgent-v3.5 等闭源系统在 AndroidWorld 上达到 ~70% 成功率，但**所有轨迹数据完全封闭**。开源社区依赖 AndroidControl、AMEX 等公开数据集，训练的模型只能达到 ~30%（如 ScaleCUA、UI-S1），差距悬殊且原因不明。

核心挑战有两方面：
1. **任务指令多样性不足**：现有方法将探索与生成耦合，依赖单条轨迹作为上下文，多样性受限于局部观察
2. **轨迹缺乏错误恢复信号**：专家蒸馏只教"正确路径"，不教"如何从错误中恢复"，导致测试时性能差距

## 方法/架构

OpenMobile 提出两个核心创新：

### 1. 解耦任务合成（Decoupled Task Synthesis）
- **探索阶段**：先遍历 App 功能构建全局环境记忆（Global Environment Memory）
- **生成阶段**：利用短期记忆（相邻屏幕）+ 长期记忆（语义相关功能）组合复杂多步指令
- 关键优势：全局视角支持跨功能组合，产生更多样化的指令

### 2. 策略切换轨迹推演（Policy-Switching Rollout）
- 在 learner 和 expert 模型之间交替执行
- **错误干预切换**（Error-Intervention Switching）：监控器检测偏离时触发专家纠正
- 生成包含错误恢复示范的轨迹，弥补纯专家蒸馏的盲区

### 数据规模
- 20 个 Android App 上合成 2.8K 任务指令，34K 动作步骤

## 实验结果

| 模型 | AndroidWorld | AndroidLab | MobileWorld |
|------|-------------|------------|-------------|
| Qwen2.5-VL-7B + OpenMobile | **51.7%** | 改善 | 9.4%→**17.4%** |
| Qwen3-VL-8B + OpenMobile | **64.7%** | 改善 | →**17.4%** |
| 闭源系统（参考） | ~70% | — | — |
| 开源基线（ScaleCUA等） | ~30% | — | — |

关键发现：
- **功能覆盖率是成功的核心驱动力**：解耦合成比耦合合成覆盖更多 App 功能，测试任务成功率与功能覆盖度正相关
- **排除数据污染**：透明实验证明性能提升来自广泛功能覆盖和错误恢复能力，而非 benchmark 过拟合

## 关键洞察

1. **开放 vs 闭源的"数据配方"比数据量更重要**：OpenMobile 用 2.8K 指令就接近了闭源系统用数十万条数据的效果，说明合成方法的创新比单纯堆数据更有效

2. **错误恢复是被忽视的训练信号**：传统方法只教"怎么做对"，但实际使用中用户会犯错、网络会卡、UI 会变化。错误恢复训练是缩小 open-closed 差距的关键

3. **全局环境记忆 vs 局部轨迹**：解耦探索和生成的设计哲学值得其他 Agent 领域借鉴——先建立全局理解，再生成局部行动

4. **对移动端的意义**：开源方案达到 64.7% 成功率意味着在手机上运行高性能 GUI Agent 已不再是闭源系统的专利，端侧部署可行性大增

## 为什么重要

OpenMobile 是 2026 年移动 Agent 领域最重要的开源贡献之一。它：
- **缩小了 open-closed 差距**：从 30% vs 70% 到 65% vs 70%
- **提供了可复现的合成方法**：所有数据和代码开源
- **建立了数据质量分析框架**：功能覆盖率分析方法可推广到其他 Agent 场景
- **推动端侧 Agent 民主化**：Qwen3-VL-8B 等中小模型即可达到实用水平，利于手机端部署

## 关联

- [[clawmobile-agentic]] — 原生移动 Agent 架构，OpenMobile 提供的数据可增强此类系统
- [[pspa-bench-gui-agent]] — GUI Agent 评测基准，OpenMobile 在此类 benchmark 上验证了效果
- [[secagent-mobile-gui]] — 屏幕理解技术，与 OpenMobile 的视觉输入处理互补
- [[exectune-guide-core-policy]] — Guide 模型引导执行策略，与 OpenMobile 的策略切换思路相关
- [[mga-memory-gui-agent]] — 记忆驱动 GUI Agent，OpenMobile 的全局环境记忆理念类似
- [[mobiflow-benchmark]] — 移动 Agent 基准测试
