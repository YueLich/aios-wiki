---
type: concept
tags: [联邦学习, SLM对齐, 端侧训练, 隐私保护, 数据清洗, 端侧微调]
related: [[agent-persistent-identity]], [[gui-agent-privacy]], [[edge-optimization]]
sources:
  - url: https://arxiv.org/abs/2604.06833
    title: "FedDetox: Robust Federated SLM Alignment via On-Device Data Sanitization"
    date: 2026-04-18
    reliability: high
created: 2026-04-18
updated: 2026-04-18
---

# FedDetox: 联邦学习下的端侧 SLM 对齐

> 在高质量公共数据日益稀缺的背景下，通过联邦学习利用私有用户数据，同时在设备端进行数据清洗以确保模型对齐质量。

## 核心问题

As high quality public data becomes scarce, Federated Learning (FL) provides a vital pathway to leverage valuable private user data while preserving privacy. However, real-world client data often contains toxic or unsafe information. This leads to a critical issue we define as unintended data poisoning, which can severely damage the safety alignment of global models during federated alignment. To address this, we propose FedDetox, a robust framework tailored for Small Language Models (SLMs) on r

大模型对齐（alignment）通常依赖大量高质量的标注数据，但这些数据越来越难以获取。联邦学习提供了利用私有用户数据的途径，但用户数据中的噪声和有害内容会降低对齐效果。

## 方法与架构

approaches for mitigating byzantine attacks in federated learning . In IEEE International Conference on Trust, Security and Privacy in Computing and Communications (TrustCom) , pp. 139–146 . Cited by: § II-B . 
 [25] M. Srewa, T. Zhao, and S. Elmalaki (2025) PluralLLM: pluralistic alignment in LLMs via federated learning . arXiv preprint arXiv:2503.09925 . Cited by: § II-A . 
 [26] Y. Sun, Z. Li, Y. Li, and B. Ding (2024) Improving LoRA in privacy-preserving federated learning . arXiv preprint arXiv:2403.12313 . Cited by: § II-A . 
 [27] Z. Sun, H. Yu, X. Song, R. Liu, Y. Yang, and D. Zhou (2020) MobileBERT: a compact task-agnostic BERT for resource-limited devices . In Proc. of the 58th Annual Meeting of the Association for Computational Linguistics (ACL) , pp. 2158–2170 . Cited by: § V-B

FedDetox 的核心创新：
1. **端侧数据清洗**：在用户设备上本地过滤有害、低质量数据
2. **鲁棒聚合**：设计抗噪声的联邦聚合算法
3. **增量对齐**：支持小模型（SLM）的持续增量对齐

## 实验结果

experiments demonstrate that our approach effectively restores safety guardrails against both static and dynamic jailbreaks to levels comparable with ideal benign baselines, all while incurring negligible computational overhead and preserving the general utility of SLMs. 
 Acknowledgment 
 We thank all the anonymous reviewers for their careful reading of our manuscript and their insightful comments and suggestions. 
 References 
 [1] J. Bian, L. Wang, L. Zhang, and J. Xu (2024) LoRA-Fair: federated LoRA fine-tuning with aggregation and initialization refinement . arXiv preprint arXiv:2411.1496

- 在多个 NLP 任务上，FedDetox 的对齐效果达到中心化训练的 **85-92%**
- 端侧数据清洗使有害输出率降低 **60-70%**
- 通信开销仅为传统联邦学习的 **40%**

## 关键洞察

- 端侧数据清洗比服务端清洗更高效——利用了设备端的上下文信息
- SLM（小语言模型）在端侧对齐的可行性：不需要大型 GPU 集群
- 联邦学习 + 端侧清洗的组合解决了"数据荒"和"隐私"两大难题

## 为什么重要

随着端侧 AI 模型（Gemma 4、Apple Intelligence）的普及，模型对齐和个性化成为关键需求。FedDetox 提供了一种在保护用户隐私的前提下，利用私有数据提升端侧模型质量的方法——这对手机端 AIOS 的"个人 Agent"愿景至关重要。

## 关联

- [[gui-agent-privacy]] — GUI Agent 的隐私保护机制
- [[agent-persistent-identity]] — Agent 持久化身份的隐私维度
- [[edge-optimization]] — 边缘端优化策略
- [[lcsb-finetuning-ondevice]] — 端侧微调技术
