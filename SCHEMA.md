---
domain: 手机端 AI操作系统 (Mobile AIOS)
owner: hermes-agent
created: 2026-04-14
version: 2.0
---

# Mobile AIOS Wiki — 知识图谱 Schema

## 领域定义
核心主题: 手机端AI操作系统 — 端侧大模型部署、手机AI助手、AI原生OS架构、NPU/端侧芯片、端侧多模态、量化/蒸馏/剪枝、隐私计算与端云协同

## Wiki 结构
- entities/ — 实体页面（公司、产品、模型）
- concepts/ — 概念页面（技术、方法）
- comparisons/ — 对比页面
- queries/ — 常见问题速查
- raw/ — 原始资料（articles, papers, transcripts, assets）

## 页面格式
每个 .md 文件必须包含 YAML frontmatter（type, tags, related, sources, created）+ 至少 2 个 wikilink

## 更新策略
- 增量更新：只添加新内容，不删除已有内容
- 更新而非重建：已有页面只做 append/patch，不覆写
