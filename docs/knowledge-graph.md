---
type: query
tags: [index, graph, overview]
created: 2026-04-14
updated: 2026-04-14
---

# 🗺️ 知识图谱总览

> Mobile AIOS 知识库中所有实体和概念的关系网络。

## 核心主题

### 推理与部署
- [[mnn-350]] — 阿里端侧推理引擎
- [[llamacpp-b8791]] / [[ggml-llamacpp-hf]] — llama.cpp 生态
- [[gemma-cpp-inference]] — Gemma C++ 推理
- [[coremltools-9]] — Apple 模型转换
- [[edgeflow-cold-start]] — 冷启动优化
- [[react-native-llm-edge]] — 跨平台推理

### 模型
- [[gemma4-ondevice]] — Google 端侧多模态
- [[gemini-flash-live]] — 实时音频 AI
- [[minicpm-242]] — 面壁端侧模型
- [[qwen35-small]] — 千问端侧系列

### Agent 系统
- [[clawmobile-agentic]] — 分层架构，确定性优先（EuroMLSys 2026）
- [[secagent-mobile-gui]] — 语义增强 GUI Agent
- [[mga-memory-gui-agent]] — 记忆驱动 Agent
- [[gui-agent-privacy]] — 隐私保护
- [[pspa-bench-gui-agent]] — 个性化评估
- [[turing-test-mobile-gui]] — 拟人化评估

### 优化技术
- [[kv-cache-quantization-ondevice]] — KV-Cache 优化
- [[septq-post-training-quantization]] — 后训练量化
- [[lcsb-finetuning-ondevice]] — 端侧微调
- [[multimodal-edge-pruning]] — 零样本剪枝

### 应用
- [[mana-mobile-ad-detection]] — 广告检测
- [[melotune-ondevice-music]] — 音乐推荐
- [[facelivtv2-mobile-face]] — 人脸识别
- [[fastshade-mobile-denoising]] — 图像去噪
- [[sense-less-infer-more]] — 边缘医疗

## 关键关系

推理框架 ←→ 模型 ←→ Agent
   ↑           ↑        ↑
  硬件协同   量化优化   评估基准

- **推理框架** 为 **模型** 提供运行时
- **Agent** 依赖 **推理框架** 执行
- **优化技术** 贯穿全栈
- **评估基准** 验证系统

## 趋势

1. 确定性 + 概率性协同成为共识
2. KV-Cache 量化是端侧推理关键瓶颈
3. GUI Agent 从实验室走向真实设备
4. 隐私保护变为核心设计约束
