---
title: "SkillLearnBench: Benchmarking Continual Learning Methods for Agent Skill Generation on Real-World Tasks"
arXiv: 2604.20087
date: 2026-04-22
tags: [agent-memory, continual-learning]
reviewer: auto
source: arXiv RSS/API
---

# SkillLearnBench: Benchmarking Continual Learning Methods for Agent Skill Generation on Real-World Tasks

## 论文基本信息

- **作者**: Shanshan Zhong, Yi Lu, Jingjie Ning, Yibing Wan, Lihan Feng, +5 more
- **arXiv**: https://arxiv.org/abs/2604.20087
- **领域**: cs.CL


## 摘要

Skills have become the de facto way to enable LLM agents to perform complex real-world tasks with customized instructions, workflows, and tools, but how to learn them automatically and effectively remains unclear. We introduce SkillLearnBench, the first benchmark for evaluating continual skill learning methods, comprising 20 verified, skill-dependent tasks across 15 sub-domains derived from a real-world skill taxonomy , evaluated at three levels: skill quality, execution trajectory, and task outcome. Using this benchmark, we evaluate recent continual learning techniques, those leveraging one-shot, self/teacher feedback, and skill creator to generate skills from agent experiences. We find that all continual learning methods improve over the no-skill baseline, yet consistent gains remain elusive: no method leads across all tasks and LLMs, and scaling to stronger LLMs does not reliably help. Continual learning improves tasks with clear, reusable workflows but struggles on open-ended tasks, and using stronger LLM backbones does not consistently produce better skills. Our analysis also revealed that multiple iterations in continual learning facilitate genuine improvement via external feedback, whereas self-feedback alone induces recursive drift. Our data and code are open-source at https://github.com/cxcscmu/SkillLearnBench to enable further studies of automatic skill generation and continual learning techniques.

## 核心贡献

1. （待补充：基于摘要提炼 3-5 条核心贡献）
2. 
3. 

## 研究背景与问题

（待补充：论文要解决的核心问题是什么？为什么这个问题重要？）

## 核心方法

（待补充：论文的核心方法/技术方案）

## 为什么重要

（待补充：论文的主要贡献和意义）

## 与移动端/端侧相关性

（待补充：该研究与端侧/移动端 Agent 记忆系统的关联）
