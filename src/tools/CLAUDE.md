# Tools 模块 · 工具系统

> P2 | src/tools/ 模块文档

## 模块职责

**Tools 模块** 实现 Claude Code 的所有可用工具（30+），包括文件操作、 shell 执行、网络请求、MCP 集成、任务管理等。每个工具都有独立的权限控制和执行逻辑。

---

## 成员列表

### 核心工具

| 工具目录 | 职责 |
|----------|------|
| `BashTool/` | Shell 命令执行（含权限控制） |
| `FileReadTool/` | 文件读取 |
| `FileEditTool/` | 文件编辑（diff/patch） |
| `FileWriteTool/` | 文件写入 |
| `GlobTool/` | 文件模式匹配 |
| `GrepTool/` | 文本搜索 |

### Agent 和任务

| 工具目录 | 职责 |
|----------|------|
| `AgentTool/` | Agent 调用和编排 |
| `TaskCreateTool/` | 任务创建 |
| `TaskGetTool/` | 任务获取 |
| `TaskListTool/` | 任务列表 |
| `TaskOutputTool/` | 任务输出 |
| `TaskStopTool/` | 任务停止 |
| `TaskUpdateTool/` | 任务更新 |
| `TeamCreateTool/` | 团队创建 |
| `TeamDeleteTool/` | 团队删除 |

### MCP 集成

| 工具目录 | 职责 |
|----------|------|
| `MCPTool/` | MCP 工具调用 |
| `ListMcpResourcesTool/` | MCP 资源列表 |
| `ReadMcpResourceTool/` | MCP 资源读取 |
| `McpAuthTool/` | MCP 认证 |

### 网络和搜索

| 工具目录 | 职责 |
|----------|------|
| `WebFetchTool/` | 网页抓取 |
| `WebSearchTool/` | 网络搜索 |
| `LSPTool/` | 语言服务器协议 |

### 会话和模式

| 工具目录 | 职责 |
|----------|------|
| `EnterPlanModeTool/` | 进入计划模式 |
| `ExitPlanModeTool/` | 退出计划模式 |
| `EnterWorktreeTool/` | 进入工作树 |
| `ExitWorktreeTool/` | 退出工作树 |
| `REPLTool/` | REPL 交互 |

### 用户交互

| 工具目录 | 职责 |
|----------|------|
| `AskUserQuestionTool/` | 向用户提问 |
| `SendMessageTool/` | 发送消息 |

### 配置和管理

| 工具目录 | 职责 |
|----------|------|
| `ConfigTool/` | 配置管理 |
| `SkillTool/` | 技能调用 |
| `ScheduleCronTool/` | 定时任务 |
| `SleepTool/` | 延迟执行 |

### 其他工具

| 工具目录 | 职责 |
|----------|------|
| `BriefTool/` | 简报生成 |
| `NotebookEditTool/` | Notebook 编辑 |
| `PowerShellTool/` | PowerShell 执行 |
| `RemoteTriggerTool/` | 远程触发 |
| `SyntheticOutputTool/` | 合成输出 |
| `TodoWriteTool/` | TODO 管理 |
| `ToolSearchTool/` | 工具搜索 |

### 共享代码

| 目录 | 职责 |
|------|------|
| `shared/` | 工具共享逻辑 |
| `testing/` | 测试工具 |
| `AgentTool/built-in/` | 内置 Agent |

---

## 依赖关系

```
[FROM] 依赖:
  - src/types/ (类型定义)
  - src/services/ (服务层)
  - src/utils/permissions/ (权限控制)
  - src/utils/sandbox/ (沙箱执行)

[TO] 被消费于:
  - src/coordinator/ (协调器)
  - src/tasks/ (任务系统)
  - src/commands/ (命令实现)

[HERE] 位置:
  - src/tools/ 位于源码核心层
  - 每个工具独立目录，便于权限隔离
```

---

## 工具接口规范

每个工具遵循统一接口：

```typescript
interface Tool {
  name: string;
  description: string;
  inputSchema: JsonSchema;
  execute(params: object): Promise<ToolResult>;
  requiresPermission?: PermissionType;
}
```

---

## 权限分级

1. **只读工具** — FileRead, Glob, Grep (无需审批)
2. **写入工具** — FileEdit, FileWrite (需用户审批)
3. **执行工具** — Bash, PowerShell (需用户审批 + 沙箱)
4. **网络工具** — WebFetch, WebSearch (可配置限制)
5. **系统工具** — MCP, LSP (需配置授权)

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
