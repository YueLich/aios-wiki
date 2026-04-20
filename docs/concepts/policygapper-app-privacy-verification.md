---
type: concept
tags: [privacy, mobile, llm, google-play, app-security, compliance, automated-verification]
related: [[anonymization-gui-agent-privacy]], [[genai-smartphone-privacy-perception]], [[gui-agent-privacy]]
sources:
  - url: https://arxiv.org/abs/2604.16128
    title: "PolicyGapper: Automated Detection of Inconsistencies Between Google Play Data Safety Sections and Privacy Policies Using LLMs"
    date: 2026-04-17
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# PolicyGapper: LLM 驱动的应用隐私合规验证

> 基于 LLM 的自动化工具，检测 Google Play 商店应用的数据安全声明 (DSS) 与其隐私政策 (PP) 之间的不一致。在 330 个应用中发现了 2,689 项遗漏声明，其中 80% 的流行应用存在不完整或误导性的 DSS 声明。

## 核心问题

2022 年起，Google 要求所有 Play 商店应用提交 Data Safety Section (DSS)——标准化的数据收集、使用和共享声明。然而：
- 编写准确的 DSS 声明具有挑战性，必须与隐私政策 (PP) 保持一致
- 先前研究表明**近 80% 的流行应用**包含不完整或误导性的 DSS 声明
- 目前没有自动化工具验证 DSS 与 PP 之间的一致性
- 手动审查每个应用的合规性成本极高

## 方法/架构

### 四阶段流水线（无需访问应用二进制文件）

1. **Scraping (抓取)**
   - 从 Google Play 抓取 DSS 声明
   - 从应用官网抓取隐私政策文本

2. **Pre-processing (预处理)**
   - 文本清理和结构化
   - 将 DSS 和 PP 分解为可比对的声明单元

3. **Analysis (分析)**
   - 使用 LLM 对比 DSS 声明与 PP 内容
   - 识别：DSS 中声明但 PP 中未提及的项目
   - 识别：PP 中描述但 DSS 中遗漏的项目
   - 覆盖数据收集和数据共享两个维度

4. **Post-processing (后处理)**
   - 结果聚合和验证
   - 生成结构化的差异报告

### 技术特点
- **无需应用二进制**: 仅依赖公开信息（Google Play 页面 + 隐私政策网页）
- **LLM 驱动**: 利用大语言模型的语义理解能力进行声明对比
- **全品类覆盖**: 评估了全部 33 个 Google Play 品类中的 330 个头部应用

## 实验结果/关键数据

### 规模
| 指标 | 数值 |
|------|------|
| 评估应用数 | 330 个（Q3 2025 Top 排名） |
| 覆盖品类 | 33 个（全部 Google Play 品类） |
| 识别遗漏声明总数 | 2,689 项 |
| 数据收集遗漏 | 2,040 项 |
| 数据共享遗漏 | 649 项 |

### 验证性能（分层 10% 子集，3 轮独立运行平均）
| 指标 | 值 |
|------|-----|
| Precision | 0.75 |
| Recall | 0.77 |
| Accuracy | 0.69 |
| F1-score | 0.76 |

### 关键发现
- **数据收集遗漏远多于数据共享遗漏** (2040 vs 649): 开发者更难全面披露收集行为
- **80% 流行应用存在 DSS 不一致**: 验证了先前研究的结论
- **跨品类普遍性**: 问题不局限于特定应用类型

## 关键洞察

1. **LLM 在合规验证中的新角色**: PolicyGapper 展示了 LLM 作为"监管科技" (RegTech) 工具的潜力——自动化的语义级合规检查，而不仅仅是文本生成。

2. **隐私声明的系统性失败**: 80% 的应用存在不一致，说明当前的隐私声明机制存在结构性问题。标准化表单 (DSS) 的初衷与实际执行之间存在巨大鸿沟。

3. **对端侧 AI 的影响**: 随着端侧 AI 应用增加（如 [[loudreader-ondevice-tts]] 等完全离线应用），隐私声明变得更加复杂——端侧推理的数据处理边界需要新的披露框架。

4. **开源可复现性**: 项目在 GitHub 上开源 (Mobile-IoT-Security-Lab/PolicyGapper)，包含数据集、提示词、源代码和结果。

## 为什么重要

对手机端 AIOS 生态而言：

- **AI 驱动的隐私审计**: 随着端侧 AI 能力增强，应用的隐私声明复杂度也在增加。PolicyGapper 模式可以扩展为端侧 AI 应用的隐私合规检查工具。

- **移动应用生态治理**: 80% 的应用隐私声明不一致是一个系统性问题。自动化检查是实现大规模隐私合规的唯一可行路径。

- **LLM 端侧部署的隐私场景**: 如果将 PolicyGapper 的检查逻辑部署到端侧（使用小型 LLM），用户可以在自己的设备上审计已安装应用的隐私合规性，无需将数据发送到云端。

## 关联

- [[anonymization-gui-agent-privacy]] — GUI Agent 的隐私保护策略
- [[genai-smartphone-privacy-perception]] — 用户对 GenAI 手机的隐私感知
- [[gui-agent-privacy]] — GUI Agent 隐私保护的系统性分析
