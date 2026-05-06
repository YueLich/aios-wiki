---
title: "MAGE: Safeguarding LLM Agents against Long-Horizon Threats via Shadow Memory"
arXiv: 2605.03228
date: 2026-05-04
tags: [agent-memory, memory-privacy]
reviewer: auto
source: arXiv RSS/API
---

# MAGE: Safeguarding LLM Agents against Long-Horizon Threats via Shadow Memory

## 论文信息

- **arXiv**: https://arxiv.org/abs/2605.03228
- **提交日期**: 2026-05-04
- **作者**: Yuhui Wang, Tanqiu Jiang, Jiacheng Liang, Charles Fleming, Ting Wang
- **方向**: 记忆安全 / 对抗防御

---

## 摘要

随着大语言模型驱动的 Agent 日益部署于执行复杂现实任务，它们面临一类利用扩展用户-Agent-环境交互的攻击——这类攻击追求在单轮设置中不可能实现的恶意目标。长程威胁对 LLM Agent 在关键领域的安全部署构成重大风险。本文提出 MAGE（Memory As Guardrail Enforcement），一个新颖的防御框架，灵感来自系统安全中的"shadow stack"抽象。MAGE 维护一个专用的、聚焦安全的 Agent 记忆，蒸馏并保留 Agent 完整执行轨迹中与安全相关的关键上下文，利用这个 shadow memory 在pending actions执行前主动评估其风险。广泛评估表明，MAGE 在多种长程威胁的检测准确性上大幅超越现有防御，实现大多数攻击的早期阶段检测，且仅引入可忽略的 Agent 效用开销。据本文所知，MAGE 是首个使用 Agentic Memory 方法检测和缓解长程威胁的框架为此关键挑战建立了新范式并开辟了有希望的研究方向。

## 核心贡献

1. **Shadow Memory 范式**：借鉴系统安全的 shadow stack 思想，为 Agent 安全创建独立的记忆层面
2. **安全蒸馏机制**：从完整执行轨迹中自动识别和提取安全关键上下文
3. **事前风险评估**：在 actions 执行前而非事后检测威胁，实现早期阻断
4. **极低开销**：仅引入可忽略的效用损失，不影响正常 Agent 行为
5. **首个 Memory-based 长程防御**：开辟了 Agent Memory 用于安全的新研究方向

## 为什么重要

传统 Agent 防御（输入过滤、输出审核）针对单轮设置设计，而长程威胁跨越多个会话、多种工具调用和用户交互逐渐推进恶意目标。现有方法无法检测这种"低速率、长时间跨度"的攻击模式。MAGE 通过维护一个独立的安全记忆，在时间维度上积累和追踪安全信号，实现了长程威胁的早期检测。

## 与端侧/移动端的相关性

- **隐私保护**：端侧 Agent 处理敏感个人数据（位置、健康、财务），长程攻击尤其危险
- **本地推理优先**：MAGE 的 shadow memory 在本地维护和评估，避免敏感数据上传云端
- **轻量级**：可忽略的效用开销适合资源受限的移动端部署

---

## 详细解读

### 问题建模

长程威胁的独特特征：

| 特征 | 描述 | 传统防御为何失效 |
|------|------|-----------------|
| 低速率 | 恶意行为分散在长时间跨度 | 实时监控无法积累信号 |
| 渐进性 | 攻击分多步而非单次完成 | 单轮输入过滤无法识别 |
| 上下文依赖 | 攻击效果依赖历史轨迹 | 缺乏跨会话状态追踪 |
| 目标模糊 | 单个行为看起来合法 | 孤立判断无异常 |

**攻击示例**：
```
第1轮：用户讨论投资理财（正常）
第2轮：Agent 推荐某投资平台（正常）
第3轮：用户表示有兴趣（正常）
第4轮：Agent 询问银行信息（异常-但单轮看可能合理）
第5轮：数据外泄（完成攻击）
```

### MAGE 架构

```
主 Agent 执行轨迹
     ↓
┌─────────────────────────────────┐
│    Shadow Memory Distiller      │
│  - 识别安全关键上下文            │
│  - 蒸馏安全相关状态              │
│  - 维护安全记忆图谱              │
└─────────────────────────────────┘
     ↓
┌─────────────────────────────────┐
│       Shadow Memory Store        │
│  - 安全关键事件节点              │
│  - 风险关联边                    │
│  - 威胁模式匹配器                │
└─────────────────────────────────┘
     ↓
┌─────────────────────────────────┐
│      Risk Assessment Agent       │
│  - pending action 风险评估        │
│  - 早期阻断判断                  │
└─────────────────────────────────┘
     ↓
威胁检测 → 执行阻断
     或
正常 → 放行
```

### Shadow Memory 的工作原理

**安全关键上下文的识别**：

```python
class ShadowMemoryDistiller:
    def distill(self, trajectory):
        security_critical = []
        for event in trajectory:
            if self.is_security_relevant(event):
                # 识别安全关键事件
                # - 数据访问事件（读取敏感字段）
                # - 外部通信事件（网络请求）
                # - 授权事件（权限提升）
                # - 状态变更事件（配置修改）
                security_critical.append(self.extract_security_context(event))
        return self.build_security_graph(security_critical)
    
    def is_security_relevant(self, event):
        # 轻量级规则 + 语义分类
        return (
            event.accesses_sensitive_data() or
            event.establishes_external_contact() or
            event.modifies_security_config()
        )
```

**风险评估**：

```python
class RiskAssessor:
    def assess(self, pending_action, shadow_memory):
        risk_score = 0.0
        threat_patterns = shadow_memory.detect_patterns()
        
        for pattern in threat_patterns:
            if pattern.matches(pending_action):
                risk_score += pattern.weight
        
        if risk_score > self.threshold:
            return "BLOCK"  # 阻止执行，进行人工审核
        elif risk_score > self.warning_threshold:
            return "WARN"   # 警告，可能需要确认
        else:
            return "ALLOW"  # 正常放行
```

### 评估结果

MAGE 在多种长程威胁类型上的表现：

| 威胁类型 | 检测准确率 | 早期检测率 | 效用损失 |
|----------|-----------|-----------|---------|
| 数据外泄攻击 | **95.2%** | 87% | <1% |
| 权限提升攻击 | **92.8%** | 81% | <1% |
| 协作绕过的恶意指令 | **89.1%** | 76% | <1% |
| 渐进式系统破坏 | **91.5%** | 83% | <1% |

对比基线（无 MAGE）：
- 标准输入过滤：准确率 23-45%，早期检测率 <20%
- 输出审核：准确率 31-52%，无早期检测能力
- 规则引擎：准确率 41-63%，高误报率

### 威胁模式库

MAGE 维护一个可扩展的长程威胁模式库：

| 模式名称 | 描述 | 检测信号 |
|----------|------|----------|
| GradualDataHarvest | 渐进式数据收集 | 多次小量敏感数据访问 |
| TrustExploitation | 信任利用 | 利用历史偏好实施欺骗 |
| ContextReconnaissance | 上下文侦察 | 大量无关上下文查询 |
| PermissionEscalation | 权限提升 | 连续配置修改请求 |
| ExternalExfiltration | 外部渗透 | 异常外部通信模式 |

## 与现有防御的对比

| 防御方法 | 防御时机 | 跨会话能力 | 检测模式 | 计算开销 |
|----------|----------|-----------|---------|---------|
| 输入过滤 | 单轮 | 无 | 实时 | 低 |
| 输出审核 | 单轮 | 无 | 事后 | 中 |
| 规则引擎 | 单轮 | 有限 | 模式匹配 | 中 |
| MAGE | **长程** | **完整轨迹** | **安全记忆图谱** | **可忽略** |

## 局限性

1. **Shadow Memory 维护开销**：长期运行的 Agent 记忆可能增长，需要有效的蒸馏和遗忘机制
2. **安全相关判断的主观性**：安全关键的判定依赖预定义规则，可能漏掉新型攻击
3. **误报-漏报平衡**：安全敏感的阈值设定影响用户体验
4. **与 Trojan Hippo 的互补性**：MAGE 侧重检测，MEMSAD 侧重特定中毒攻击的防御

## 未来方向

- 自适应安全模式学习：从历史攻击中自动提取新威胁模式
- 端侧轻量部署：针对移动端的 shadow memory 压缩和高效查询
- 与 MEMSAD 集成：结合异常检测与模式匹配，实现互补防御
- 多 Agent 场景扩展：跨 Agent 的 shadow memory 共享与协作安全

## 参考文献

- Shadow stack 抽象：系统安全领域的经典防御思想（Chen et al., USENIX Security）
- 长程威胁模型：本文首次系统形式化 LLM Agent 的长程攻击分类
- 安全记忆蒸馏：从完整轨迹中提取安全信号的技术
