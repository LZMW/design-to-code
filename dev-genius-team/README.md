# Dev-Genius (开发天才)

### 新一代 AI 驱动的全自动软件开发团队

![版本](https://img.shields.io/badge/版本-1.0.0-blue?style=for-the-badge)
![架构](https://img.shields.io/badge/架构-黑板%20%2B%20事件总线-orange?style=for-the-badge)
![专家](https://img.shields.io/badge/智能体-5位专家-purple?style=for-the-badge)

**基于黑板模式与事件驱动架构的全自动软件开发多智能体协作框架**

---

## 项目简介

**Dev-Genius** 是 design-interrogator-team 的下游开发团队。它接收上游设计文档，自动规划、开发、测试、审查，完成从设计到代码的全流程。

### 核心创新

| 特性 | 说明 |
|------|------|
| 🧠 **智能协调** | 读取 DI 设计文档，自动选择最优执行路径 |
| 📋 **黑板模式** | 共享工作区消除冗余上下文传递，降低 50%+ Token 消耗 |
| ⚡ **事件总线** | 发布-订阅模式实现异步通信 |
| 🔄 **局部闭环** | Developer ↔ QA Tester 快速 Bug 修复循环 |
| 🔁 **/goal + /loop 集成** | 关键节点推荐 /goal（终点）+ /loop（节奏）命令，支持全自动开发 |
| 📥 **DI 无缝衔接** | 自动读取 design-interrogator 产出，零手动转换 |

---

## 与 Design-Interrogator 的衔接

```
┌─────────────────────────┐     ┌─────────────────────────┐
│ Design-Interrogator     │     │ Dev-Genius             │
│ (设计阶段)               │ ──▶  │ (开发阶段)               │
│                         │     │                         │
│ .di/phases/             │     │ .dev-genius/blackboard/ │
│ 03_documentation/       │     │ ├── task-queue.md       │
│   ARCHITECTURE.md ──────┼───▶ │ ├── architecture.md     │
│   MODULE_SPEC.md ───────┼───▶ │ ├── code-state.md       │
│   ADR/*.md ─────────────┼───▶ │ ├── test-report.md      │
│   DECISION_TREE.md ─────┼───▶ │ ├── review-report.md    │
│                         │     │ └── INDEX.md            │
└─────────────────────────┘     └─────────────────────────┘
```

---

## 精英战队

| 角色 | 代号 | 核心能力 | 触发词 |
|:----:|------|----------|--------|
| 🎯 **规划师** | Planner | 读取DI文档、任务分解、排期规划 | `规划`, `排期`, `任务分解` |
| 🏛️ **架构师** | Architect | 技术架构细化、接口设计、ADR | `架构`, `设计`, `接口` |
| 💻 **开发者** | Developer | 功能实现、Bug修复、代码重构 | `开发`, `实现`, `修复` |
| 🧪 **测试师** | QA Tester | 测试设计、回归测试、Bug报告 | `测试`, `QA`, `验证` |
| 🔍 **审查师** | Analyst | 代码评审、安全审计、性能分析 | `审查`, `评审`, `审计` |

---

## 执行模式

### 模式一：全流程流水线
```
Planner → Architect → Developer → QA Tester → Analyst
```
适用：新项目全流程开发

### 模式二：Dev↔QA 局部闭环
```
QA Tester 发现 Bug → Developer 修复 → QA Tester 复测 → [通过/继续]
```
适用：Bug修复、质量保障

### 模式三：单专家独立
```
单专家直接执行（规划/架构/开发/测试/审查）
```
适用：特定环节独立任务

---

## /goal + /loop 全自动开发

Dev-Genius 在每个关键节点推荐两条命令互补使用：

| 命令 | 作用 | 语法 |
|------|------|------|
| `/goal` | 设定终点，一直工作直到条件满足 | `/goal [完成条件]` |
| `/loop` | 设定节奏，按间隔重复执行 | `/loop [间隔] [命令]` |

**组合使用**：先 `/goal` 定终点，再 `/loop` 定节奏。

```
[规划完成]
    ├── 🎯 /goal 所有任务完成+测试通过+审查无Critical
    └── 💡 /loop 10m 逐任务执行 → [任务1] → /loop 5m → [任务2] → ... → [交付]
```

**示例**：

```
🎯 推荐 /goal 命令：
/goal task-queue.md 中的所有开发任务已完成，全部测试通过，审查无 Critical 问题

💡 推荐 /loop 命令：
/loop 10m /dev-genius-coordinator 读取 INDEX.md，从 task-queue.md 取出下一个任务执行并更新进度
```

---

## 快速开始

### 前置条件
- Claude Code CLI 已安装
- design-interrogator-team 已执行（产出 .di/ 目录）

### 使用方式

```bash
# 方式1：命令触发
/dev-genius-coordinator 开发项目

# 方式2：自然语言
"帮我根据设计文档开始开发"

# 方式3：/goal + /loop 全自动
/goal task-queue.md 中所有任务完成+测试通过+审查无Critical
/loop 10m /dev-genius-coordinator 读取 task-queue.md 依次执行所有开发任务
```

---

## 文件结构

```
dev-genius-team/
├── README.md
├── INSTALL.md
├── agents/
│   ├── dev-genius-planner.md
│   ├── dev-genius-architect.md
│   ├── dev-genius-developer.md
│   ├── dev-genius-qa-tester.md
│   └── dev-genius-analyst.md
└── skills/
    └── dev-genius-coordinator/
        └── skill.md
```

---

## MCP 工具支持

| 专家 | MCP 工具 | 用途 |
|------|----------|------|
| Planner | `sequential-thinking` | 复杂项目深度规划 |
| Architect | `context7`, `sequential-thinking` | 技术选型、框架文档 |
| Developer | `context7`, `web-search`, `web-reader` | API文档、代码示例 |
| Analyst | `vision-server`, `web-reader` | UI审查、安全公告 |

---

## 版本历史

### v1.0 (2026-05-15)
- 初始版本
- 黑板型架构，5位专家
- /goal + /loop 全自动开发支持
- design-interrogator 无缝衔接
- 融合 code-vanguard + cascade + devops-corps 三队精华

---

## 致谢

- 基于 [Super Team Builder](../super-team-builder/) 框架构建
- 融合 [Code Vanguard](../code-vanguard-team/) 的混合模式设计
- 融合 [Cascade](../cascade-team/) 的流水线质量门控
- 融合 [DevOps Corps](../devops-corps-team/) 的黑板模式与事件总线
- 上游依赖 [Design Interrogator](../design-interrogator-team/) 提供设计文档
