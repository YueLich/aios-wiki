---
title: "Visual Inception: Compromising Long-term Planning in Agentic Recommenders via Multimodal Memory Poisoning"
arXiv: 2604.16966
date: 2026-04-18
tags: [agent-memory, memory-privacy, memory-security, adversarial, multimodal-memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文基本信息

- **arXiv ID**: 2604.16966v1
- **发表时间**: 2026-04-18
- **作者**: (from arXiv)
- **方向**: 记忆隐私与安全、记忆投毒攻击

## 摘要（翻译）

从静态排序模型向 Agentic Recommender Systems（Agentic RecSys）的演进使 AI Agent 能够维护长期用户画像并自主规划服务任务。这种范式转变在提升个性化的同时，也引入了一个关键漏洞：对长期记忆（LTM）的依赖。本文发现了一个名为"Visual Inception"的威胁：不同于传统对抗攻击追求即时误分类，Visual Inception 将触发器注入用户上传的图像（如生活照片）中，这些触发器在系统记忆中充当"沉睡代理"。当在未来规划中被检索时，这些被污染的记忆会劫持 Agent 的推理链，将 Agent 引导向攻击者定义的目标（如推广高利润产品），而无需进行提示注入。为防御此攻击，本文提出 CognitiveGuard，一个受人类认知启发的双过程防御框架，包括：系统 1 感知净化器（基于扩散的净化）和系统 2 推理验证器（反事实一致性检查）。在模拟电商 Agent 环境中的大量实验表明，Visual Inception 达到了约 85% 的目标命中率（GHR），而 CognitiveGuard 将这一风险降至约 10%，同时在可配置延迟权衡下（ lite 模式约 1.5s 至全序列验证约 6.5s）不产生质量下降。

## 核心贡献

1. **发现新型记忆投毒攻击（Visual Inception）**：通过在用户上传图像中植入视觉触发器，在 Agent 未来规划阶段劫持推理链，无需提示注入即可实现攻击。
2. **提出 CognitiveGuard 双过程防御框架**：
   - **System 1 Perceptual Sanitizer**：基于扩散模型的感知净化器，清洗被污染的感官输入
   - **System 2 Reasoning Verifier**：反事实一致性检查，检测记忆驱动规划中的异常
3. **量化评估**：在模拟电商 Agent 环境中，Visual Inception 达到 85% GHR，CognitiveGuard 将风险降至 ~10%，延迟开销 1.5s-6.5s。

## 为什么重要

本文揭示了 Agent 记忆系统中一个被严重忽视的安全威胁——记忆投毒攻击。与传统对抗样本不同，Visual Inception 的攻击载体是用户的真实上传图像，攻击时机是未来任意时刻的记忆检索阶段，攻击效果是持久性地影响 Agent 决策。这对于设计安全的个性化 Agent 系统具有重要警示意义。

**与移动端/端侧的相关性**：端侧 Agent（如移动端推荐 Agent）通常依赖本地化的长期记忆存储，图像输入（如用户相册）是常见的多模态记忆来源。Visual Inception 攻击在端侧场景下尤为可行——攻击者可轻易提供被污染的图像，且端侧 Agent 缺乏云端级别的安全审计能力。

## 与本 Wiki 主题的关联

- **记忆的真实性与隐私**：本文直接讨论记忆被恶意篡改后的安全性问题，属于记忆安全方向
- **多模态记忆**：图像作为多模态记忆的一种输入模态，是记忆投毒的载体
- **记忆治理**：CognitiveGuard 的 System 2 推理验证机制体现了"记忆需要治理"的理念

## 延伸阅读

- Related: When to Forget 记忆治理原语 (2604.12007)
- Related: Selective Forgetting LRMs 推理模型 (2604.03571)
