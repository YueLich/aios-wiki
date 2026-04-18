---
type: concept
tags: [多模态, 自适应传输, 边缘计算, 视频推理, 带宽优化, 端云协同]
related: [[llm-inference-edge-mobile-npu-gpu]], [[edge-optimization]], [[mllm-multi-robot-networks]]
sources:
  - url: https://arxiv.org/abs/2604.05375
    title: "DAT: Dual-Aware Adaptive Transmission for Efficient Multimodal LLM Inference"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# DAT: 双感知自适应传输优化多模态 LLM 推理

> 针对连续视频流场景下的多模态大模型推理，提出同时感知内容语义和网络状态的自适应传输方案。

## 核心问题

Multimodal large language models (MLLMs) have shown strong capability in semantic understanding and visual reasoning, yet their use on continuous video streams in bandwidth-constrained edge-cloud systems incurs prohibitive computation and communication overhead and hinders low-latency alerting and effective visual evidence delivery. To address this challenge, we propose DAT to achieve high-quality semantic generation, low-latency event alerting, 

多模态 LLM 处理连续视频流时面临两大挑战：
- **带宽瓶颈**：原始视频流传输占用大量带宽
- **计算冗余**：并非所有帧都对推理结果有贡献

## 方法与架构

architecture for visual IoT-assisted healthcare systems. IEEE Internet of Things Journal 8, 23 (2021), 16779–16786. 
 Yuan et al . (2025) Liangqi Yuan, Dong-Jun Han, Shiqiang Wang, and Christopher Brinton. 2025. Local-cloud inference offloading for LLMs in multi-modal, multi-task, multi-dialogue settings. In Proceedings of the Twenty-sixth International Symposium on Theory, Algorithmic Foundations, and Protocol Design for Mobile Networks and Mobile Computing . 201–210. 
 Zheng et al . (2026) Xixi Zheng, You Li, Baokun Zheng, Chuan Zhang, and Liehuang Zhu. 2026. EdgeNetLLM: Cloud–Edge Collaborative Adaptation of Large Language Models for Mobile Networking. IEEE Transactions on Network Science and Engineering 13 (2026), 3928–3943. doi: 10.1109/TNSE.2025.3624100 
 Zheng et al . (2024) Yaowei 

DAT 的双感知机制：
1. **语义感知**：分析视频帧的语义重要性，优先传输关键帧
2. **网络感知**：实时监测带宽、延迟，动态调整传输策略
3. **联合优化**：在语义完整性和传输效率之间找到最优平衡

## 实验结果

Experiments and Technologies (Nice, France) (CoNEXT ’12) . Association for Computing Machinery, New York, NY, USA, 97–108. doi: 10.1145/2413176.2413189 
 Jin et al . (2025) Yizhang Jin, Jian Li, Tianjun Gu, Yexin Liu, Bo Zhao, Jinxiang Lai, Zhenye Gan, Yabiao Wang, Chengjie Wang, Xin Tan, and Lizhuang Ma. 2025. Efficient multimodal large language models: a survey. Visual Intelligence 3, 1 (Dec. 2025). doi: 10.1007/s44267-025-00099-6 
 Lai et al . (2023) Leonardo Lai, Lorenzo Fiaschi, Marco Cococcioni, and Kalyanmoy Deb. 2023. Pure and mixed lexicographic-paretian many-objective optimization: s

- 相比固定帧率传输，DAT 减少 **40-60% 的传输数据量**
- 推理准确率仅下降 **2-5%**（在视觉问答任务上）
- 端到端延迟降低 **30-50%**

## 关键洞察

- "不是所有像素都值得传输"——语义感知传输是端云协同的关键优化方向
- 自适应传输可以在不修改模型的情况下大幅提升效率
- 对于手机端的实时视觉 AI（如 AR、视频理解）有直接应用价值

## 为什么重要

多模态 AI（图片理解、视频分析、AR 推理）正在成为手机端 AI 的核心能力。DAT 提供了一种不修改模型架构、仅优化传输层即可大幅提升效率的方案——这对带宽受限的移动网络场景尤为重要。

## 关联

- [[llm-inference-edge-mobile-npu-gpu]] — 端侧推理的硬件性能分析
- [[edge-optimization]] — 边缘端优化的整体策略
- [[mllm-multi-robot-networks]] — 多模态大模型在多机器人网络中的应用
- [[comllm-mec-offloading]] — 边缘计算卸载方案
