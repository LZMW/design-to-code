# Installation Guide

## 文件位置

将以下文件放置到对应目录：

### 协调器 Skill

```
文件: skills/design-interrogator-coordinator/skill.md
→ 放到: ~/.claude/skills/design-interrogator-coordinator/skill.md
```

### 专家 Agent 配置

```
文件: agents/design-interrogator-analyst.md
→ 放到: ~/.claude/agents/design-interrogator-analyst.md

文件: agents/design-interrogator-interrogator.md
→ 放到: ~/.claude/agents/design-interrogator-interrogator.md

文件: agents/design-interrogator-writer.md
→ 放到: ~/.claude/agents/design-interrogator-writer.md
```

## 安装步骤

### 1. 复制协调器 Skill

```bash
mkdir -p ~/.claude/skills/design-interrogator-coordinator
cp skills/design-interrogator-coordinator/skill.md ~/.claude/skills/design-interrogator-coordinator/skill.md
```

### 2. 复制专家 Agent 配置

```bash
mkdir -p ~/.claude/agents
cp agents/design-interrogator-analyst.md ~/.claude/agents/
cp agents/design-interrogator-interrogator.md ~/.claude/agents/
cp agents/design-interrogator-writer.md ~/.claude/agents/
```

### 3. 验证安装

重启 Claude Code 后，输入以下任一命令测试：

```
分析一个项目源码
拷问我
```

协调器应自动激活并开始工作流程。

## 依赖

### MCP 服务器（可选但推荐）

- **Context7** — 用于查询框架/库官方文档。如未安装，团队仍可使用内置工具完成工作，但涉及知名框架的分析和咨询质量可能下降。

### 内置工具（无需额外安装）

所有专家均使用 Claude Code 内置工具：Read、Write、Edit、Glob、Grep、Bash、LSP。

## 权限配置

如需减少权限提示，可在项目 `.claude/settings.json` 中添加：

```json
{
  "permissions": {
    "allow": [
      "Read(**)",
      "Write(**)",
      "Glob(**)",
      "Grep(**)",
      "Bash(git:*)",
      "Bash(ls:*)"
    ]
  }
}
```

---

**版本**: 1.1
