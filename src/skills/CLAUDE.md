# Skills 模块 · 技能系统

> P2 | src/skills/ 模块文档

## 模块职责

**Skills 模块** 实现技能系统，包括内置技能加载、技能目录管理、MCP 技能构建器等。技能是可复用的 Agent 能力模块，支持用户自定义扩展。

---

## 成员列表

### 核心文件

| 文件 | 职责 | 行数 |
|------|------|------|
| `loadSkillsDir.ts` | 技能目录加载器 | ~850 行 |
| `bundledSkills.ts` | 内置技能管理 | ~180 行 |
| `mcpSkillBuilders.ts` | MCP 技能构建器 | ~40 行 |

### 内置技能 (`bundled/`)

| 技能 | 职责 |
|------|------|
| `batch.ts` | 批处理技能 |
| `claudeApi.ts` | Claude API 技能 |
| `claudeApiContent.ts` | Claude API 内容技能 |
| `claudeInChrome.ts` | Chrome 集成技能 |
| `debug.ts` | 调试技能 |
| `keybindings.ts` | 键位绑定技能 |
| `loop.ts` | 循环执行技能 |
| `loremIpsum.ts` | 占位文本技能 |
| `remember.ts` | 记忆技能 |
| `scheduleRemoteAgents.ts` | 远程 Agent 调度 |
| `simplify.ts` | 简化技能 |
| `skillify.ts` | 技能化技能 |
| `stuck.ts` | 卡住检测技能 |
| `updateConfig.ts` | 配置更新技能 |
| `verify.ts` | 验证技能 |
| `verifyContent.ts` | 内容验证技能 |
| `index.ts` | 技能索引 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/tools/SkillTool/ (技能工具)
  - src/services/mcp/ (MCP 服务)
  - src/utils/ (工具函数)
  - fs/promises (文件系统)

[TO] 被消费于:
  - src/commands/skills/ (技能命令)
  - src/tools/SkillTool/ (技能执行)
  - 用户通过技能命令调用

[HERE] 位置:
  - src/skills/ 位于功能扩展层
  - 连接工具层和用户自定义能力
```

---

## 技能系统架构

### 技能加载流程

```
1. 扫描技能目录 (~/Skills, 项目根目录/.skills)
2. 解析技能定义 (SKILL.md, skill.json)
3. 注册技能到技能池
4. 用户通过 /skills 命令调用
```

### 技能定义格式

```markdown
---
name: my-skill
description: 技能描述
triggers: 触发关键词
---

# 技能指令

详细说明技能如何工作...
```

---

## 关键功能

### 内置技能 (`bundledSkills.ts`)
- 预装技能集合
- 无需用户配置即可使用
- 支持热加载和更新

### 技能目录加载 (`loadSkillsDir.ts`)
- 扫描多个技能目录
- 支持用户自定义技能
- 技能冲突处理
- 技能依赖解析

### MCP 技能构建 (`mcpSkillBuilders.ts`)
- 从 MCP 服务器动态构建技能
- 支持远程技能调用
- MCP 协议适配

---

## 技能类型

1. **内置技能** — 随应用分发的预装技能
2. **用户技能** — 用户自定义技能（~/Skills/）
3. **项目技能** — 项目级技能（.skills/）
4. **MCP 技能** — 从 MCP 服务器动态加载

---

## 技能调用

```bash
# 列出所有技能
/skills list

# 调用技能
/skills my-skill --arg value

# 安装技能
/skills install <url>
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
