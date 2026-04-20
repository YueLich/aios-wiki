---
type: concept
tags: [LiDAR, 非视距感知, 移动设备, 数据集, 深度感知, iPhone]
related: [[denali-nlos-lidar-dataset]]
sources:
  - url: https://arxiv.org/abs/2604.16201
    title: "DENALI: A Dataset Enabling Non-Line-of-Sight Spatial Reasoning with Low-Cost LiDARs"
    date: 2026-04-22
    reliability: high
created: 2026-04-20
updated: 2026-04-20
---

# DENALI: 低成本 LiDAR 非视距空间感知数据集

> 首个大规模真实世界低-cost LiDAR 时空直方图数据集，证明消费级 LiDAR 可实现数据驱动的非视距感知

## 核心问题

iPhone 12 Pro 及以上的手机都配备了 LiDAR 传感器（用于自动对焦、人像模式、AR），但这些传感器的潜力远超深度测量：
- **隐藏信息**：LiDAR 发射短激光脉冲后，传感器记录的时间分辨多弹跳光返回包含视野外物体的信息
- **非视距（NLOS）感知**：利用"间接光"看到角落、障碍物后面的世界
- **低成本 LiDAR vs 科研 LiDAR**：消费级 LiDAR（如手机/机器人的）只能输出单个深度值，但内部记录了完整的时空直方图

问题：如何利用消费级低成本 LiDAR 的内部数据实现 NLOS 感知？

## 方法架构

**DENALI 数据集**：
- **72,000 个隐藏物体场景**的大规模真实世界数据
- 使用低-cost LiDAR 捕获时间分辨 LiDAR 直方图
- 覆盖多样化物体形状、位置、光照条件和空间分辨率
- 首个真实世界低-cost LiDAR NLOS 数据集

**数据驱动 NLOS 感知**：
- 利用深度学习从时空直方图中推断隐藏物体
- 识别关键场景和建模因素对性能的限制
- 发现仿真-真实转换保真度差距

## 关键洞察

**为什么重要**：
- **手机端隐藏能力释放**：数十亿部手机的 LiDAR 传感器有未开发的 NLOS 感知能力
- **安全应用**：NLOS 感知可应用于紧急响应、自动驾驶、机器人避障
- **数据集价值**：作为首个真实世界数据集，将推动 NLOS 研究从仿真走向实际应用
- **仿真到真实的差距**：指出了当前仿真 NLOS 研究的根本局限

**深层分析**：
- 消费级 LiDAR 的 NLOS 能力一直被忽视，因为厂商只暴露深度 API（非原始直方图）
- 72,000 个真实场景的数据集规模远超以往的仿真数据
- sim-to-real gap 的发现意味着：纯仿真训练的 NLOS 模型在真实世界中表现不佳

## 关联
- （本领域研究较新，wiki 中暂无直接关联页面）
