---
title: "llama.cpp b8837"
type: entity
created: 2026-04-19
source: github
repo: ggml-org/llama.cpp
tag: b8837
tags: [llama.cpp, inference, release, backend]
---

# llama.cpp b8837

## 基本信息

- **项目**: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)
- **版本**: b8837
- **类型**: 推理框架构建版本
- **关键变更**: ggml-backend-meta 多段读取支持

## 主要更新

### ggml-backend-meta: 多段读取支持

此版本在 `ggml-backend-meta` 中新增了 `get_tensor` 的多段读取（multi-segment read）支持（PR #22063）。

这改进了元数据后端的张量获取机制，允许从多个数据段中读取张量数据，对于分段存储的模型文件更加高效。

## 可用构建

| 平台 | 架构 | 备注 |
|------|------|------|
| macOS | Apple Silicon (arm64) | 标准构建 |
| macOS | Apple Silicon (arm64) | KleidiAI 启用 |
| macOS | Intel (x64) | — |
| iOS | XCFramework | 移动端集成 |
| Linux | x64 (CPU) | — |
| Linux | arm64 (CPU) | — |

## 版本关系

- 前序版本: [b8836](llamacpp-b8836.md), [b8833](llamacpp-b8833.md)
- 后续版本: b8838, b8839
- 项目主页: [ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp)

## 对端侧部署的意义

持续的后端改进确保了 llama.cpp 在各种平台（特别是 iOS/Android）上的模型加载效率。多段读取支持对于移动设备上常见的分段下载/存储策略尤其有价值。

## 参考链接

- [GitHub Release](https://github.com/ggml-org/llama.cpp/releases/tag/b8837)
- [PR #22063](https://github.com/ggml-org/llama.cpp/pull/22063)
