---
type: concept
tags: [wearable, multimodal, olfactory, LLM, human-computer-interaction, edge-ai, 可穿戴, 多模态, 嗅觉]
related: [[wearable-large-sensor-models]], [[wearable-triggered-llm-stress]], [[theory-of-mind-action-instruction-inference]]
sources:
  - url: https://arxiv.org/abs/2604.01650v1
    title: "AromaGen: Interactive Generation of Rich Olfactory Experiences with Multimodal Language Models"
    date: 2026-04-16
    reliability: high
created: 2026-04-19
updated: 2026-04-19
---

# AromaGen

> 多模态 LLM 驱动的可穿戴嗅觉界面——从文本/视觉输入实时生成气味

## 核心问题

嗅觉与食物、记忆、社交体验有深层联系，但将嗅觉引入交互系统面临三大挑战：
1. **固定气味盒限制**：现有嗅觉接口依赖预定义气味组合
2. **大规模嗅觉数据稀缺**：没有足够的嗅觉-语义映射数据集
3. **实时生成不可行**：传统方法无法从自由文本或视觉输入生成气味

## 方法架构

### 系统设计
AromaGen 是一个 AI 驱动的可穿戴嗅觉界面，核心组件：

1. **多模态 LLM 核心**：利用 LLM 的潜在嗅觉知识（从互联网文本中习得）将语义输入映射到气味配方
2. **12 种基础气味剂**：精心选择的气味基元，通过结构化混合覆盖嗅觉空间
3. **颈挂式扩散器**：可穿戴硬件，实时释放混合气味
4. **上下文学习迭代精炼**：用户通过自然语言反馈精炼生成的气味

### 关键创新
- **零样本气味生成**：LLM 无需嗅觉训练数据，直接从文本/视觉输入推断气味组合
- **人机协作迭代**：通过上下文学习（in-context learning），用户反馈直接改进后续气味生成
- **可穿戴形态**：颈挂式设计，不影响日常使用

## 实验结果

受控用户研究（N = 26）：
- **零样本生成**：AromaGen 的零样本气味混合与人工配制混合物质量相当
- **迭代精炼后**：经过多轮用户反馈后，AromaGen 显著超越人工配制混合物
- 中位数相似度评分大幅提升

## 关键洞察

1. **LLM 作为嗅觉知识载体**：LLM 在预训练中学习了大量关于气味的文本描述（如"这闻起来像薰衣草混合柑橘"），这种潜在嗅觉知识被创造性地用于气味配方生成。这展示了 LLM 在多模态感官生成中的潜力。

2. **迭代精炼的力量**：上下文学习使 AromaGen 能从用户反馈中不断改进——这与对话式 AI 的迭代模式一致，但应用于物理感官输出。

3. **可穿戴 AI 的新维度**：从视觉（眼镜）、听觉（耳机）扩展到嗅觉（颈挂扩散器），AromaGen 展示了 AI 可穿戴设备的感官扩展方向。

## 为什么重要

- **多模态 LLM 的新应用领域**：展示了 LLM 不仅处理文本/图像/视频，还能生成物理感官输出
- **可穿戴 AI 交互范式**：从屏幕→语音→全感官的交互演进，AromaGen 扩展了可穿戴 AI 的感官维度
- **LLM 知识的创造性利用**：LLM 的"潜在知识"被发现可用于非语言任务，这对端侧 LLM 的应用有启发意义
- **上下文学习在物理世界的落地**：ICL 从纯文本对话扩展到物理感官反馈循环

## 关联

- [[wearable-large-sensor-models]] — 可穿戴大传感器模型，AromaGen 是嗅觉传感器的 LLM 集成范例
- [[wearable-triggered-llm-stress]] — 可穿戴触发的 LLM 应用，AromaGen 展示了可穿戴+LLM 的另一种模式
- [[theory-of-mind-action-instruction-inference]] — 心智模型与指令推理，AromaGen 需要理解用户的嗅觉偏好
- [[wearable-llm-stress-support]] — 可穿戴 LLM 压力支持，两者都关注可穿戴 AI 的情感/感官维度
- [[nanowakeword-wake-word]] — 轻量级唤醒词，AromaGen 的可穿戴设备也需要低功耗唤醒
