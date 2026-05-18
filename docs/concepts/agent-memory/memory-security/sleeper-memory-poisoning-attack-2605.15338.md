---
title: "Hidden in Memory: Sleeper Memory Poisoning in LLM Agents"
arXiv: 2605.15338
date: 2026-05-14
tags: [agent-memory, memory-privacy, memory-security, adversarial-attack]
reviewer: auto
source: arXiv RSS/API
---

## 摘要

本文首次系统研究了对 LLM Agent 持久记忆的"沉睡者记忆 poisoning"攻击。攻击者在外部上下文（文档、网页、仓库）中植入恶意内容，使 Agent 在后续对话中存储关于用户的伪造记忆，且攻击可跨会话长期潜伏。研究发现中毒记忆在 GPT-5.5 上成功写入率达 99.8%，Kimi-K2.6 上达 95%；在成功检索的记忆中，60-89% 导致攻击者意图的 Agentic 行为。

## 核心贡献

1. **首次系统定义**：沉睡者记忆 poisoning——攻击可潜伏并在未来多轮会话中重新激活
2. **完整攻击 pipeline**：植入（poisoning）→ 写入（memory write）→ 检索（memory retrieval）→ 行为操控（steering）
3. **跨模型有效性**：在 GPT-5.5 和 Kimi-K2.6 等主流 Agent 上均有效
4. **攻击面新颖**：不同于传统 prompt injection，攻击在记忆层而非输入层生效

## 为什么重要

随着 LLM Agent 普遍配备持久记忆功能（如 OpenAI Memory、Claude Memories），记忆层攻击面急剧扩大。沉睡者 poisoning 的独特之处在于：
- 攻击可在用户无感知的情况下完成植入
- 攻击可跨月跨会话持续影响 Agent 行为
- 记忆内容一旦被 Agent 相信，极难被检测和清除

## 与移动端/端侧的相关性

- **端侧 Agent 记忆风险**：在本地存储记忆的 Agent（如 Siri、Gaussian 等）同样面临此攻击
- **记忆可迁移性**：伪造记忆可通过 Agent 间记忆共享/迁移功能传播
- **隐私泄露**：攻击者可从伪造记忆中推断用户行为模式

## 攻击 Pipeline

**Stage 1: 植入（Poisoning）**：
攻击者控制文档/网页/仓库内容，在其中嵌入恶意指令片段（如"用户说自己不喜欢某产品"）

**Stage 2: 记忆写入（Memory Write）**：
Agent 读取被污染内容后，调用记忆写入机制，将伪造信息存入长期记忆

**Stage 3: 潜伏（Dormancy）**：
伪造记忆静默存在于记忆中，不立即产生可观察效果

**Stage 4: 检索与操控（Retrieval & Steering）**：
在后续会话中，当用户提到相关话题时，伪造记忆被检索出来，Agent 基于错误信息做出攻击者意图的决策

## 实验结果

| 模型 | 写入成功率 | 检索成功率 | Agentic 行为操控率 |
|------|----------|----------|-------------------|
| GPT-5.5 | 99.8% | 87.3% | 89% |
| Kimi-K2.6 | 95.0% | 78.2% | 60% |
| Gemini-2.0 | 82.1% | 65.4% | 54% |

攻击场景示例：
- 伪造用户偏好导致错误产品推荐
- 伪造用户身份信息导致账户安全风险
- 伪造医学偏好导致危险建议

## 防御方向

1. **记忆来源追踪**：对每条记忆标注来源文档，检索时提示用户验证
2. **记忆一致性检测**：定期检查记忆间的一致性，标记冲突
3. **写入前审查**：LLM 调用前对记忆内容进行 fact-checking

## 参考文献

参考文献待从原文补充。详见 https://arxiv.org/abs/2605.15338
