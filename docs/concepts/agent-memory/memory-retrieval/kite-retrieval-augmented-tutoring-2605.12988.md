---
title: "Retrieval-Augmented Tutoring for Algorithm Tracing and Problem-Solving in AI Education"
arXiv: 2605.12988
date: 2026-05-13
tags: [agent-memory, memory-retrieval, RAG, education]
reviewer: auto
source: arXiv RSS/API
---

# 核心贡献

1. **KITE 系统**：Knowledge-Informed Tutoring Engine，基于多模态 RAG 的智能辅导系统，服务于算法推理和问题解决的课堂教学助手。
2. **意图感知苏格拉底响应策略**：使用 intent-aware Socratic response strategy，根据不同学生需求提供针对性提示、引导性问题和发展性脚手架。
3. **多模态 RAG pipeline**：从课程材料中检索相关信息，保持响应对课程内容的一致性。
4. **多维评估框架**：结合 RAGAs 指标、专家评估和模拟学生 pipeline 三种评估方式。

# 为什么重要

传统辅导系统难以在保持课程一致性的同时提供个性化脚手架。KITE 通过 retrieval-augmented 方式确保响应基于真实课程内容，同时通过意图感知策略提供差异化支持。

# 与端侧/移动端的相关性

智能辅导是边缘部署的重要场景——个性化学习应用需要本地处理学生交互数据。多模态 RAG 架构可迁移至移动端，为学生提供离线辅导能力。

# 标签

`memory-retrieval` `RAG` `education` `tutoring-systems` `agentic-ai`

# 核心方法

## KITE 架构

1. **意图识别**：识别学生问题类型（算法跟踪、调试、问题求解）
2. **检索增强**：从课程材料库中检索相关内容
3. **苏格拉底响应生成**：根据意图类型生成差异化提示
4. **反馈循环**：通过学生-系统多轮对话提供渐进式支持

## 评估结果

三种评估方式：
- RAGAs 指标：响应接地性和质量良好
- 专家评估：教育质量获得认可
- 模拟学生 pipeline：帮助弱模型产生更准确的跟踪和程序性问题的后续回答

# 参考文献

（参考文献待从原文补充）
