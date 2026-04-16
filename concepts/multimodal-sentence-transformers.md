---
type: concept
tags: [multimodal, embedding, reranker, sentence-transformers, huggingface, on-device, retrieval, search]
related: [[gemma4-ondevice]], [[on-device-inference]], [[mobile-aios-overview]], [[apple-intelligence]]
sources:
  - url: https://huggingface.co/blog/multimodal-sentence-transformers
    title: "Multimodal Embedding & Reranker Models with Sentence Transformers"
    date: 2026-04-09
    reliability: high
  - url: https://huggingface.co/blog/train-multimodal-sentence-transformers
    title: "Training and Finetuning Multimodal Embedding & Reranker Models"
    date: 2026-04-09
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Sentence Transformers 多模态嵌入与重排

> Sentence Transformers v5.4 新增多模态支持，可用统一 API 对文本、图像、音频、视频进行编码和跨模态相似度计算。Tom Aarsen (HuggingFace) 发布。

## 核心问题

传统嵌入模型只能处理文本，无法实现跨模态检索（如用文字搜图、用图像搜文档）。移动端场景下，用户期望在手机上实现统一的多模态搜索体验——拍照搜商品、语音搜图片、截图搜文档。

## 方法/架构

### 多模态嵌入模型
- 将不同模态（文本、图像、音频、视频）映射到**共享嵌入空间**
- 可用标准余弦相似度比较跨模态内容
- 支持 text→image、image→text、audio→text 等任意方向检索

### 多模态重排模型（Cross Encoder）
- 对混合模态对计算相关性分数
- 支持 text-image、text-audio 等组合评分
- 比嵌入模型精度更高，但计算量更大（适合精排阶段）

### API 设计
```python
# 嵌入模型 — 文本和图像统一编码
from sentence_transformers import SentenceTransformer
model = SentenceTransformer("Qwen3-VL-2B")
text_emb = model.encode("一只猫在沙发上")
image_emb = model.encode("cat.jpg")
similarity = model.similarity(text_emb, image_emb)

# 重排模型 — 混合模态评分
from sentence_transformers import CrossEncoder
reranker = CrossEncoder("Qwen3-VL-2B-reranker")
score = reranker.predict([("搜索 query", "candidate_image.jpg")])
```

### 依赖安装
```bash
pip install -U "sentence-transformers[image]"   # 图像支持
pip install -U "sentence-transformers[audio]"   # 音频支持
pip install -U "sentence-transformers[video]"   # 视频支持
```

## 关键数据

| 模型 | VRAM 需求 | 适用场景 |
|------|----------|---------|
| Qwen3-VL-2B | ~8 GB | 端侧/边缘设备 |
| Qwen3-VL-8B | ~20 GB | 服务器/桌面 GPU |

## 端侧适用性分析

**直接适用**：
- Qwen3-VL-2B（~8GB VRAM）可在高端手机 NPU 或平板 GPU 上运行
- 嵌入计算是离线批量操作，适合预建索引场景
- 端侧视觉搜索（拍商品→搜相似商品）的核心组件

**间接适用**：
- 服务端部署后通过 API 为端侧设备提供多模态搜索
- 端侧重排（小模型）+ 云端检索（大模型）的混合架构
- 与 [[gemma4-ondevice]] 结合：Gemma 4 做理解，Sentence Transformers 做检索

## 技术意义

1. **统一多模态搜索 API**：不再需要为每种模态维护独立的检索管线
2. **端侧 RAG 的关键组件**：多模态 RAG 需要跨模态检索能力，这是缺失的一环
3. **训练范式扩展**：同一套框架支持嵌入和重排两种任务的训练/微调
4. **生态整合**：与 HuggingFace transformers、datasets 生态无缝集成

## 关联

- [[gemma4-ondevice]] — 端侧多模态理解模型，可与嵌入模型互补
- [[on-device-inference]] — 端侧推理技术栈，嵌入计算需要推理框架支持
- [[apple-intelligence]] — Apple 的端侧 AI 方案，Core ML 可能集成类似能力
- [[mobile-aios-overview]] — 手机端 AIOS 总体架构
