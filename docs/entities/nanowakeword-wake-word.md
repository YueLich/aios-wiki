---
type: entity
tags: [推理框架, 唤醒词, 端侧推理, 语音AI, 嵌入式, 轻量化]
related: [[biotrain-ondevice-finetuning-mcu]], [[ahc-mcu-continual-detection]], [[lstm-gait-asic-accelerator]]
sources:
  - url: https://github.com/arcosoph/nanowakeword
    title: "NanoWakeWord: Open-source wake word training for any device"
    date: 2026-04-16
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# NanoWakeWord

> 下一代自适应唤醒词检测框架。使用少量数据训练高精度自定义唤醒词模型，适用于任何设备——从手机到微控制器。

## 核心问题

现有的唤醒词检测方案（如 Porcupine、Snowboy）要么需要付费 API，要么模型体积大、精度不稳定。NanoWakeWord 旨在提供一个开源、轻量、自适应的框架，让开发者能用最少的数据训练出高精度的自定义唤醒词模型。

## 方法/架构

### 自适应训练引擎

NanoWakeWord 的核心创新是"智能训练引擎"：
- **数据自适应**：自动分析输入音频数据的特征（噪声水平、说话人多样性、音频长度分布），调整训练策略
- **架构优化**：根据目标设备的约束（CPU/内存/延迟），自动选择模型架构（小型 CNN vs Tiny Transformer）
- **负样本增强**：自动生成困难负样本（与唤醒词发音相近的词、环境噪声），降低误唤醒率

### 模型输出

训练完成后输出：
- **ONNX 模型**：通用格式，可在任何支持 ONNX Runtime 的设备上运行
- **TFLite 模型**：针对嵌入式设备优化
- **Core ML 模型**：Apple 设备专用

### 训练流程

1. 准备正样本（唤醒词录音，建议 50-200 条）
2. 准备负样本（非唤醒音频，或使用框架自动生成）
3. 运行训练：`python -m nanowakeword.train --positive-dir data/positive --negative-dir data/negative`
4. 导出模型：`python -m nanowakeword.export --format onnx --output model.onnx`

## 关键数据

- **模型大小**：典型模型 < 1 MB（适合 MCU 部署）
- **推理延迟**：< 50ms（在 Raspberry Pi Zero 上实测）
- **误唤醒率**：< 1 次/天（在标准测试集上）
- **训练时间**：< 10 分钟（在 Colab 免费 GPU 上）

## 为什么重要

1. **端侧语音交互的民主化**：唤醒词是语音交互的第一步。NanoWakeWord 让任何开发者都能为自己的设备/应用创建自定义唤醒词，无需依赖商业 API。
2. **极致轻量化**：< 1 MB 的模型意味着可以在 MCU、智能手表、IoT 设备上运行，这是 [[biotrain-ondevice-finetuning-mcu]] 所代表的超轻量端侧 AI 趋势的一部分。
3. **隐私友好**：所有处理在设备上完成，音频数据不离开设备。

## 关联

- [[biotrain-ondevice-finetuning-mcu]] — 另一个超轻量端侧训练方案（亚 MB 级模型）
- [[ahc-mcu-continual-detection]] — MCU 上的持续目标检测，类似的资源受限场景
- [[lstm-gait-asic-accelerator]] — ASIC 加速的端侧推理，唤醒词检测也可通过硬件加速
