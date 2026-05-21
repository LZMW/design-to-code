# Dev-Genius 安装指南

## 前置条件

- Claude Code CLI 已安装
- 具有 `~/.claude/` 目录的写入权限
- （推荐）已配置的 MCP 服务器以获得增强功能
- （推荐）design-interrogator-team 已安装

## 快速安装

### 步骤1：复制协调器 Skill

```bash
mkdir -p ~/.claude/skills/dev-genius-coordinator
cp skills/dev-genius-coordinator/skill.md ~/.claude/skills/dev-genius-coordinator/skill.md
```

### 步骤2：复制专家 Agent 配置

```bash
mkdir -p ~/.claude/agents
cp agents/dev-genius-planner.md ~/.claude/agents/
cp agents/dev-genius-architect.md ~/.claude/agents/
cp agents/dev-genius-developer.md ~/.claude/agents/
cp agents/dev-genius-qa-tester.md ~/.claude/agents/
cp agents/dev-genius-analyst.md ~/.claude/agents/
```

### 步骤3：验证安装

```bash
# 检查协调器
ls ~/.claude/skills/dev-genius-coordinator/skill.md

# 检查专家
ls ~/.claude/agents/dev-genius-*.md
```

## 安装后的目录结构

```
~/.claude/
├── skills/
│   └── dev-genius-coordinator/
│       └── skill.md
└── agents/
    ├── dev-genius-planner.md
    ├── dev-genius-architect.md
    ├── dev-genius-developer.md
    ├── dev-genius-qa-tester.md
    └── dev-genius-analyst.md
```

## MCP 配置（推荐）

在 `~/.claude/settings.json` 中添加：

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    },
    "web-search-prime": {
      "command": "npx",
      "args": ["-y", "@anthropic/web-search-mcp"]
    }
  }
}
```

## 使用方法

### 触发协调器

```
/dev-genius-coordinator [任务描述]
```

### 示例命令

```
# 全流程开发
/dev-genius-coordinator 根据 .di/ 中的设计文档，开始全流程开发

# 仅执行测试
/dev-genius-coordinator 对最新代码进行测试验证

# 代码审查
/dev-genius-coordinator 对支付模块进行代码审查
```

### /goal + /loop 全自动模式

规划完成后，协调器会推荐两条互补命令：

| 命令 | 作用 | 示例 |
|------|------|------|
| `/goal` | 设定终点条件，一直工作直到满足 | `/goal 所有开发任务完成并通过测试` |
| `/loop` | 设定执行节奏，按间隔重复 | `/loop 10m /dev-genius-coordinator 继续执行` |

**组合使用**：

```
🎯 /goal task-queue.md 中的所有任务已完成，测试通过，审查无 Critical
💡 /loop 10m /dev-genius-coordinator 读取 INDEX.md，继续执行下一个任务
```

## 验证清单

- [ ] 协调器 Skill 文件存在
- [ ] 5个专家 Agent 文件存在
- [ ] 文件内容格式正确（YAML frontmatter）
- [ ] MCP 服务器已配置（如需要）
- [ ] 触发协调器能正常响应

## 与 Design-Interrogator 配合使用

完整工作流：

```bash
# Step 1: 设计阶段（Design-Interrogator）
/design-interrogator-coordinator 分析 <参考项目> 并拷问我的设计方案

# Step 2: 开发阶段（Dev-Genius）
/dev-genius-coordinator 根据 .di/ 的设计文档开始全流程开发

# Step 3: 全自动开发
/goal task-queue.md 中所有任务完成+测试通过+审查无Critical
/loop 10m /dev-genius-coordinator 继续执行开发任务
```

## 故障排查

### 问题1：协调器无法触发

检查 Skill 文件路径：`ls ~/.claude/skills/dev-genius-coordinator/skill.md`

### 问题2：专家无法被调用

检查 Agent 文件：`ls ~/.claude/agents/dev-genius-*.md`

### 问题3：无法读取 DI 文档

确认 design-interrogator-team 已执行完成，`.di/phases/03_documentation/` 目录存在。

### 问题4：MCP工具无法使用

检查 `~/.claude/settings.json` 中的 MCP 配置。

---

**版本**: v1.0
**更新时间**: 2026-05-15
