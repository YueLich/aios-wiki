---
type: concept
tags: [qwen, on-device, multimodal, small-model, alibaba, image-text-to-text, edge-inference]
related:
  - "[[minicpm-242]]"
  - "[[gemma4-ondevice]]"
  - "[[llamacpp]]"
sources:
  - https://huggingface.co/Qwen/Qwen3.5-0.8B
  - https://huggingface.co/Qwen/Qwen3.5-2B
  - https://huggingface.co/Qwen/Qwen3.5-4B
  - https://huggingface.co/Qwen/Qwen3.5-9B
  - https://huggingface.co/Qwen/Qwen3.5-35B-A3B
created: 2026-04-14
---

# Qwen 3.5 Small — 端侧多模态模型系列

阿里巴巴 Qwen 团队发布 Qwen 3.5 Small 系列，专为 **端侧部署** 设计的多模态语言模型。

## 模型矩阵

| 模型 | 参数量 | 架构 | 下载量 | 特点 |
|------|--------|------|--------|------|
| Qwen3.5-0.8B | 8 亿 | Dense | 2.6M | 最小，适配智能手表/IoT |
| Qwen3.5-2B | 20 亿 | Dense | 1.5M | 手机端平衡之选 |
| Qwen3.5-4B | 40 亿 | Dense | 2.9M | 主力端侧模型 |
| Qwen3.5-9B | 90 亿 | Dense | 5.7M | 高性能端侧，旗舰手机可跑 |
| Qwen3.5-35B-A3B | 350 亿(激活3B) | MoE | 3.6M | 稀疏 MoE，部分端侧可部署 |

所有模型均支持 **image-text-to-text**（图像+文本输入，文本输出），即原生多模态。

## 技术细节
- **许可**: Apache 2.0 — 完全开放，商用友好
- **架构**: Qwen3.5 系列（非 MoE 的 Dense 变体）
- **多模态**: 原生图像理解，非外挂视觉编码器
- **端侧兼容**: 支持 Transformers、llama.cpp、MNN、MLC-LLM 等推理框架

## 端侧部署路径

```
Qwen 3.5 Small → GGUF 量化 → llama.cpp → iPhone/Android
Qwen 3.5 Small → MNN 转换 → MNN Engine → Android
Qwen 3.5 Small → CoreML → Apple Neural Engine → iOS
Qwen 3.5 Small → MLC-LLM → 跨平台
```

## 为什么重要

Qwen 3.5 Small 是目前端侧多模态 AI 竞争的关键棋子：
1. **0.8B 的门槛极低** — 仅 8 亿参数即可跑在智能手表上，比 [[minicpm-242]] 的 2.4B 更小
2. **全系列多模态** — 不是纯文本模型 + 外挂视觉，而是原生 image-text-to-text
3. **3.6M 下载量**（35B-A3B）说明社区需求强劲
4. **Apache 2.0** — 比 Gemma 的商用限制更宽松
5. 与 [[gemma4-ondevice]] 直接竞争端侧多模态市场

端侧 AI 从"能不能跑"转向"跑多好"——Qwen 3.5 Small 系列让开发者在 0.8B 到 9B 之间有丰富选择。

## 相关
- [[minicpm-242]] — 面壁智能端侧模型，Qwen 的直接竞品
- [[gemma4-ondevice]] — Google 端侧多模态方案
- [[llamacpp]] — GGUF 推理引擎，Qwen 3.5 的主要部署路径之一
