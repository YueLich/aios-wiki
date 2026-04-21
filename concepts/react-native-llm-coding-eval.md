---
type: concept
tags: [coding-llm, react-native, quantization, llama.cpp, open-weights, benchmark, 移动开发]
related: [[ggml-llamacpp-hf]], [[gemma4-ondevice]], [[on-device-llm-privacy]]
sources:
  - url: https://arxiv.org/abs/2604.17187v1
    title: "React-ing to Grace Hopper 200: Five Open-Weights Coding Models, One React Native App, One GH200, One Weekend"
    date: 2026-04-19
    reliability: high
created: 2026-04-21
updated: 2026-04-21
---

# 编码 LLM 量化效率评估：React Native 多模型对比

> 在 NVIDIA GH200 上评估 5 个开源编码模型生成 React Native 应用的能力，发现 3-bit 量化模型超越 4-bit 版本，且 SWE-Bench 排名无法预测实际应用生成质量。

## 核心问题

开源编码模型在标准基准测试（SWE-Bench）上已接近闭源前沿系统的水平，但这些基准排名能否指导实际的产品开发任务选择？本文通过一个具体的 React Native 应用生成任务来回答这个问题。

## 实验设置

### 硬件与推理框架
- **硬件**: 单节点 NVIDIA GH200 576GB（96GB HBM3 + 480GB LPDDR5X 统一内存，72 ARMv8.2 核心）
- **推理引擎**: llama.cpp build b8797，通过 llama-server 提供服务
- **量化方案**: Unsloth Dynamic 2.0 GGUF（按张重要性感知量化，非均匀位宽）
- **MoE 卸载**: 专家 FFN 层通过 `--cpu-moe` 卸载到系统内存，注意力层和 KV cache 保留在 HBM

### 测试模型

| 模型 | 量化 | 磁盘大小 | 总参数/活跃参数 | 许可证 |
|------|------|----------|----------------|--------|
| Kimi-K2.5 | UD-Q3_K_XL | 480GB | 1T/32B | Modified MIT |
| Kimi-K2.5 | UD-Q4_K_XL | 622GB | 1T/32B | Modified MIT |
| GLM-5.1 | UD-IQ4_XS | 370GB | 754B/40B | MIT |
| Qwen3-Coder-480B | UD-Q4_K_XL | 276GB | 480B/35B | Apache 2.0 |
| DeepSeek-V3.2 | UD-Q4_K_XL | 430GB | 671B/37B | MIT |

### 任务规范
单一 prompt："create react-native app that allows user to create account and login and then count kangaroos seen per day and make sure it runs on the web"

评估维度：OOB 可运行性、凭证验证、用户数据隔离、按日计数、历史记录持久化、登出功能、Web 平台兼容性。

## 实验结果

| 功能 | Kimi Q3 | Kimi Q4 | GLM-5.1 | Qwen3-C | DS-V3.2 |
|------|---------|---------|---------|---------|---------|
| OOB 可运行 | ✓ | ✓ | ✗ | ✓ | ✗ |
| 认证验证 | ✓ | ✓ | ✓ | ✓ | ✗ |
| 用户数据隔离 | ✓ | ✓ | ✓ | ✓ | ✗ |
| 按日计数 | ✓ | 仅今日 | 仅今日 | ✗ | ✗ |
| 历史持久化 | ✓ | 7天 | ✓ | 7天 | ✗ |
| 登出功能 | ✓ | ✓ | ✓ | ✓ | ✗ |
| 生成速度 (tok/s) | 17 | 7.9 | ~15 | ~20 | ~14 |

**关键发现**：Kimi-K2.5 Q3（480GB，3-bit 量化）是唯一完全符合规范的模型，生成速度 17 tok/s，是 Q4（7.9 tok/s）的 2 倍以上。

## 三个新型部署发现

### 1. 默认 temperature=0 导致推理模型采样挂起
Aider 等代码编辑工具默认 `temperature=0` 以提高确定性，但 Kimi-K2.5（推荐 temperature=1.0/top_p=0.95）在此设置下出现多分钟推理停滞。`nvidia-smi` 显示服务器进程处于 R 状态但内存带宽利用率 0%，说明采样器在低概率 token 决策上自旋。**教训**：推理模型的采样参数不是可选的，必须按发布者的推荐配置。

### 2. 推理 token 泄漏到集成工具的文件路径解析器
DeepSeek-V3.2 的响应中，推理流的 `</think>` 标签泄漏到文件路径中，导致 Aider 将内容写入 `"Let's start with App.js:</think>App.js"` 而非 `App.js`，项目无法打包。**这是一个此前未记录的故障模式**。

### 3. 原生移动端 API 到 Web 平台的适配是普遍训练数据缺陷
所有 5 个模型在 Web 平台安全性上都失败了——`Alert.alert`（React Native 原生 API）在 Web 上阻塞。这表明训练数据中 React Native Web 适配的示例严重不足。

## 两大架构流派

本文识别出 2026 年 4 月开源编码模型的两大架构流派：

| 流派 | 活跃参数 | 典型硬件 | SWE-Bench 表现 | 成本比 |
|------|----------|----------|---------------|--------|
| **效率派** | 10-15B | 消费级 GPU | 等效 | 1x |
| **规模派** | 32-40B | 机构级硬件（400GB+） | 等效 | ~7x |

效率派在 SWE-Bench 上达到与规模派相当的结果，但硬件成本约为 1/7。这对端侧部署和资源受限场景有重要参考价值。

## 为什么重要

1. **量化悖论**: 3-bit 量化模型（Kimi Q3）在实际任务中超越 4-bit 版本，说明更低的量化精度可能通过增加随机性反而提升创造性代码生成质量
2. **基准误导**: SWE-Bench Pro 排名最高的 GLM-5.1（58.4%）做出了最差的产品决策（Firebase 企业方案 vs 简单本地认证），说明标准基准无法预测实际产品任务表现
3. **推理 token 泄漏**: 一个此前未记录的故障模式，对所有使用推理模型 + 代码集成工具的团队都有警示意义
4. **React Native 生态**: 暴露了所有模型在 Web 适配上的训练数据缺口，对移动端跨平台开发有直接影响

## 关联
- [[ggml-llamacpp-hf]] — 本文使用 llama.cpp b8797 进行推理，展示了 MoE 卸载模式
- [[gemma4-ondevice]] — 另一个开源模型评估，关注端侧部署
- [[on-device-llm-privacy]] — 端侧 LLM 部署的隐私考量
- [[agent-system-memory-taxonomy]] — Agent 系统的多模型选择策略
