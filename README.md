# 设计审问官 + 开发天才

> 从设计到代码的双团队协作框架 —— 经典版（Classic Edition）

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Teams](https://img.shields.io/badge/teams-2-orange)]()
[![Agents](https://img.shields.io/badge/agents-8-purple)]()

---

## 概述

这是「神机营」项目的前身——两个独立但紧密协作的 AI 专家团队，覆盖从架构设计到代码实现的完整流程。

| 团队 | 版本 | 类型 | 专家数 | 职责 |
|------|------|------|--------|------|
| **[Design-Interrogator](design-interrogator-team/)** | v1.1 | 流水线型 | 3 | 源码分析 → 设计拷问 → 文档撰写 |
| **[Dev-Genius](dev-genius-team/)** | v1.0 | 黑板型 | 5 | 任务规划 → 架构实施 → 开发 → 测试 → 审查 |

## 工作流程

```
Design-Interrogator                    Dev-Genius
(设计审问官)                            (开发天才)

源码分析 ──→ 设计拷问 ──→ 文档撰写 ──→ 任务规划 ──→ 架构实施 ──→ 开发 ──→ 测试 ──→ 审查
                                                              ↕ (局部闭环)
                                          .di/phases/03_documentation/  →  .dev-genius/blackboard/
```

## 经典版特点

- **成熟可靠**：经过验证的稳定版本，无复杂回退机制和世代日志
- **简洁清晰**：DI 专注架构设计，Dev-Genius 专注开发实现
- **黑板模式**：Dev-Genius 使用黑板 + 事件总线架构，支持 Dev↔QA 局部闭环
- **交互式拷问**：DI 的 Interrogator 支持多轮延续对话

## 安装

```bash
git clone https://github.com/LZMW/design-to-code.git
cd design-to-code

# 安装协调器
cp design-interrogator-team/skills/design-interrogator-coordinator/skill.md ~/.claude/skills/
cp dev-genius-team/skills/dev-genius-coordinator/skill.md ~/.claude/skills/

# 安装 Agent
cp design-interrogator-team/agents/*.md ~/.claude/agents/
cp dev-genius-team/agents/*.md ~/.claude/agents/
```

## 使用

```bash
# Step 1: 架构设计
/design-interrogator-coordinator 分析 G:/参考项目 的源码，然后拷问我新项目的设计，最后产出开发文档

# Step 2: 开发实现
/dev-genius-coordinator 根据设计文档开始开发
```

## 与神机营的关系

本仓库是 [神机营 (shenjiying)](https://github.com/LZMW/shenjiying) 的前身。神机营在此基础上新增了：
- **UXUI-Studio**：UX 设计团队（5 专家）
- **Karpathy 四原则**：嵌入所有团队的审查标准
- **回退机制**：三级回退 + GENESIS.md 世代日志
- **双上游衔接**：Dev-Genius 同时读取 DI + UXS 产出

如果你不需要 UX 设计能力，经典版是更简洁的选择。

## 许可

MIT License
