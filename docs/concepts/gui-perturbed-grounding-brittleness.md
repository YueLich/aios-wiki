---
type: concept
tags: [gui-agent, grounding, robustness, benchmark, domain-randomization, spatial-reasoning, on-device]
related: [[secagent-mobile-gui]], [[pspa-bench-gui-agent]], [[lamo-scalable-gui-agents]], [[turing-test-mobile-gui]], [[fedgui-federated-gui-agents]]
sources:
  - url: https://arxiv.org/abs/2604.14262
    title: "GUI-Perturbed: Domain Randomization Reveals Systematic Brittleness in GUI Grounding Models"
    date: 2026-04-15
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# GUI-Perturbed: GUI Grounding 的系统性脆弱性

> 一个受控扰动框架，揭示了当前 GUI grounding 模型在空间推理和视觉变化下的系统性脆弱性。arXiv: 2604.14262

## 核心问题

GUI grounding 模型在标准基准（ScreenSpot-v2）上报告超过 85% 的准确率，但这些分数无法反映实际部署的可靠性。问题在于现有基准每次只用一张固定截图和一个固定指令评估，忽略了真实环境中视觉场景和指令表达的多样性。

当指令从直接命名（"点击提交按钮"）变为空间推理（"点击 X 上方的按钮"）时，模型准确率从 85% 骤降至 35%。一个 70% 的浏览器缩放就能让声称 85% 准确率的模型显著退化。

## 方法/架构

**GUI-Perturbed** 是一个受控扰动框架，沿两个独立轴线系统性地变化：

### 三类扰动变体
| 变体 | 描述 | 样本数 |
|------|------|--------|
| Original | Mind2Web MHTML 通过 Playwright 渲染 | 390 |
| Style Randomized | 随机化 CSS 样式（颜色、字体、布局） | 390 |
| Text Shrink + Precision | 缩小文本并增加精度要求 | 390 |

### 指令类型
- **直接指令**：通过文本或类型直接命名目标元素
- **关系指令**：通过空间关系（"在 X 上方"、"在 Y 左侧"）定位目标

### 评估模型
评估了同架构系谱（UI-TARS 系列）中的三个 7B 模型，确保结果不受架构差异干扰。

## 实验结果

### 三个核心发现

**1. 空间推理系统性崩溃**
- 关系指令导致所有模型准确率下降 27-56 个百分点
- 这不是噪声，而是所有模型的系统性缺陷

**2. 视觉启发式是静态的**
- 70% 浏览器缩放产生统计显著性的性能退化
- 模型学会了在特定缩放下识别元素，但无法泛化

**3. LoRA 微调反而退化**
- Rank-8 LoRA SFT + 增强数据不提升反而降低性能
- 模型过拟合扰动伪影，而非学习不变性

### 训练实验关键发现
| 实验 | 结果 |
|------|------|
| 6.5k → 25k 数据缩放 | 更多数据导致更差性能（灾难性遗忘 + 过拟合） |
| 真实 vs 合成数据 | 都退化，但方式不同：真实数据均匀退化，合成数据在特定扰动类型上过拟合 |
| 文本缩小+精度 | 最大退化（~3.3 pp），尽管这应该是"最温和"的扰动 |
| ScreenSpot-v2 掩盖失败 | 标准基准能检测整体退化，但无法隔离哪些鲁棒性轴受影响 |

### 为什么标准基准不够
ScreenSpot-v2 只检测整体退化的信号，但无法告诉开发者是空间推理、视觉启发式还是推理校准出了问题。GUI-Perturbed 提供诊断粒度。

## 关键洞察

**核心洞察：85% 的准确率是误导性的。** 这些数字来自对每个截图只用一个固定指令评估的基准。实际部署中，用户可能用多种方式描述同一个元素，浏览器可能有不同的缩放级别，UI 样式可能被自定义主题改变。

**训练食谱是瓶颈**，不是数据来源。基线对比显示，RL + grounding 特定奖励比 SFT 更有效地改善空间鲁棒性。这意味着简单的数据增强策略对 GUI grounding 不够。

**对移动 Agent 的意义**：移动设备上的 GUI Agent 面临更严重的这些问题——屏幕更小、UI 更多样化、用户指令更口语化。在部署前必须用 GUI-Perturbed 类方法验证鲁棒性。

## 为什么重要

- **对手机端 AIOS 生态**：GUI Agent 是手机端智能体的核心能力，空间推理崩溃意味着 Agent 在复杂 UI 导航场景中会系统性失败
- **对模型选型**：不能仅凭 ScreenSpot 分数选模型，必须测试空间推理和视觉鲁棒性
- **对训练策略**：简单的 LoRA 微调 + 数据增强不足以改善 GUI grounding 鲁棒性，需要更高级的训练方法（如 RL + grounding 奖励）

## 关联
- [[secagent-mobile-gui]] — SecAgent 同样关注移动 GUI 的安全性和鲁棒性
- [[pspa-bench-gui-agent]] — PSPA-Bench 是另一个 GUI Agent 评估基准
- [[lamo-scalable-gui-agents]] — LAMO 关注可扩展的 GUI Agent 架构
- [[turing-test-mobile-gui]] — 图灵测试方法评估 GUI Agent 的真实能力
- [[fedgui-federated-gui-agents]] — FedGUI 研究联邦 GUI Agent，面临类似的鲁棒性挑战
