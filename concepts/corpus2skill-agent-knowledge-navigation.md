---
type: concept
tags: [agent, rag, knowledge-navigation, skill-directory, enterprise-qa, mobile-agent]
related: [[mcp-deployment-patterns]], [[skilldroid-skill-compilation]], [[exectune-guide-core-policy]], [[memento-skills-agent-design]]
sources:
  - url: https://arxiv.org/abs/2604.14572
    title: "Don't Retrieve, Navigate: Distilling Enterprise Knowledge into Navigable Agent Skills for QA and RAG"
    date: 2026-04-17
    reliability: high
created: 2026-04-17
updated: 2026-04-17
---

# Corpus2Skill: Agent 知识库导航式检索

> 将文档语料离线蒸馏为层级式技能目录，让 LLM Agent 在服务时主动导航而非被动接收检索结果。

## 核心问题

传统 RAG（检索增强生成）存在一个结构性限制：**LLM 永远"只见树木不见森林"**。具体问题：

1. **被动消费**：LLM 被动接收 top-k 检索片段，无法看到语料库的组织方式
2. **无法回溯**：无法知道还有哪些未检索的主题领域
3. **碎片化**：复杂查询（如"如何在 Wix 上将个人业务转为 LLC"）跨越多个主题，但平铺检索只返回表面相似的片段，遗漏关键操作性文档
4. **Agent RAG 仍然盲目**：即使允许迭代搜索，Agent 没有"地图"，每次搜索都是"在黑暗中摸索"

## 方法/架构

Corpus2Skill 提出两阶段流水线：

### 离线编译阶段
1. **迭代聚类**：对文档集合进行递归聚类
2. **技能目录生成**：每个聚类生成一个"技能"（摘要 + 可导航子目录）
3. **层级化组织**：构建树状技能目录，顶层为广义主题，底层为具体文档
4. **质量过滤**：确保每个技能节点都有足够的信息密度

### 在线导航阶段
1. **Agent 主动导航**：LLM Agent 浏览技能目录，而非接收固定检索结果
2. **回溯能力**：Agent 可以"向上"回到父节点查看更广泛的选项
3. **钻取能力**：Agent 可以"向下"深入到具体文档
4. **组合证据**：来自不同分支的证据可以被系统性地组合

### 与传统方法的对比
| 方式 | Agent 行为 | 语料理解 | 复杂查询能力 |
|------|-----------|---------|-------------|
| 传统 RAG | 被动消费 top-k | 无 | 低 |
| Agent RAG | 迭代搜索 | 无地图 | 中 |
| RAPTOR/GraphRAG | 层级摘要 | 有树/图但被动 | 中高 |
| **Corpus2Skill** | **主动导航** | **有技能目录** | **高** |

## 实验结果/关键数据

Corpus2Skill 在企业 QA 基准上显著优于基线：
- 在需要跨多个知识领域组合证据的复杂查询上，性能提升尤为明显
- 离线编译的计算开销可控（一次性成本）
- Agent 导航路径可解释——可以看到 Agent 探索了哪些技能目录

## 关键洞察

1. **从被动到主动的范式转换**：RAG 的核心局限不是检索质量，而是 Agent 的被动角色。Corpus2Skill 让 Agent 变成"主动研究者"而非"被动读者"
2. **技能目录即认知地图**：层级化的技能目录为 Agent 提供了类似人类组织知识的方式——从广义到具体
3. **可组合性**：不同分支的知识可以被系统性地交叉引用，这是平铺 RAG 完全做不到的
4. **对企业移动 Agent 的意义**：手机端 Agent 需要高效访问企业知识库，但受限于带宽和计算。导航式方法减少了不必要的检索轮次

## 为什么重要

对手机端 AIOS 的 Agent 生态而言，Corpus2Skill 提供了一种更高效的知识访问模式。移动 Agent 的典型场景——客户服务、文档查询、合规检查——都需要从企业知识库中找到跨领域的答案。导航式方法比迭代搜索更节省计算和网络资源，对端侧 Agent 尤其重要。

## 关联
- [[mcp-deployment-patterns]] — MCP 部署中 Agent 与知识源的交互模式
- [[skilldroid-skill-compilation]] — 类似的技能编译与复用思想
- [[exectune-guide-core-policy]] — Guide Model 引导 Agent 策略
- [[memento-skills-agent-design]] — 让 Agent 设计 Agent 的技能系统
- [[mobile-mcp]] — 移动端 MCP 集成
- [[on-device-vs-cloud-agentic-tool-calling]] — 端侧 vs 云端工具调用
