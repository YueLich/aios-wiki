---
title: "LongSeeker: Elastic Context Orchestration for Long-Horizon Search Agents"
arXiv: "2605.05191"
date: "2026-05-06"
tags: [agent-memory, memory-compression, context-management, working-memory]
reviewer: auto
source: arXiv RSS/API
---

## 论文速览

**核心问题**: 长时域搜索 Agent 需要在推理、调用工具、观察信息的过程中管理快速膨胀的工作上下文。简单地累积所有中间内容会压垮 Agent，增加成本和错误风险。

**核心贡献**: 提出 Context-ReAct 范式，引入五个原子操作（Skip、Compress、Rollback、Snippet、Delete）实现弹性上下文编排。基于此开发 LongSeeker，在四个搜索基准上大幅超越 Tongyi DeepResearch 和 AgentFold。

## 核心思想

### Context-ReAct 范式

Context-ReAct 将推理、上下文管理和工具调用统一到一个循环中，提供五个原子操作：

| 操作 | 功能 | 适用场景 |
|------|------|---------|
| **Skip** | 跳过无关观察，不写入上下文 | 过滤噪声信息 |
| **Compress** | 压缩已解析信息为摘要 | 减少 token 消耗 |
| **Rollback** | 回退到历史检查点 | 纠正错误分支 |
| **Snippet** | 提取关键片段保留 | 保留重要证据 |
| **Delete** | 删除无用分支 | 控制上下文大小 |

### 理论基础

- **Compress 操作表达完全性**: 证明 Compress 能表达任何其他操作的主要功能
- **其他操作提供效率和保真度保证**: 专门的 Skip/Delete 比通用压缩更高效
- **降低生成成本和幻觉风险**: 通过主动管理上下文减少无关信息干扰

### LongSeeker 系统

基于 Context-ReAct 范式微调的 Agent：
- **基座模型**: Qwen3-30B-A3B
- **训练数据**: 10k 合成轨迹
- **任务类型**: 长时域搜索

## 技术细节

### 上下文管理策略

LongSeeker 根据当前任务相关性动态维护不同细节级别的轨迹部分：

```
高相关性 → 保留原始细节（Snippet/Skip）
中相关性 → 压缩保留（Compress）
低相关性 → 删除（Delete）
过时分支 → 回退（Rollback）
```

### 实验结果

| 基准 | LongSeeker | Tongyi DeepResearch | AgentFold |
|------|-----------|---------------------|-----------|
| BrowseComp | **61.5%** | 43.2% | 36.2% |
| BrowseComp-ZH | **62.5%** | 46.7% | 47.3% |

大幅超越基线系统，验证了弹性上下文管理的有效性。

## 为什么重要

1. **首个完整范式**: 将工作上下文管理形式化为可证明的原子操作集合
2. **实用系统**: 不仅有理论，还有在真实长时域搜索任务上大幅超越商业系统的实践
3. **成本意识**: 通过主动管理上下文降低 LLM 调用成本（减少 token 消耗）
4. **可靠性提升**: 减少无关信息干扰，降低幻觉风险

## 与端侧/移动端的相关性

- **低计算开销**: 原子操作轻量，适合资源受限环境
- **减少云端依赖**: 本地决策哪些信息保留/删除
- **隐私保护**: 不必要的信息可以立即删除，不留痕迹
- **长对话场景**: 适合移动端个人助手的长时对话管理

## 核心贡献

1. **Context-ReAct 范式**: 统一的弹性上下文编排框架
2. **五个原子操作**: Skip/Compress/Rollback/Snippet/Delete
3. **LongSeeker 系统**: 基于 Qwen3-30B-A3B 微调的实践系统
4. **理论保证**: Compress 表达完全性 + 其他操作的效率保证

## 参考文献

- Context management in LLM agents
- Working memory models
- Long-horizon reasoning tasks
