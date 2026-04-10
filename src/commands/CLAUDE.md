# Commands 模块 · 命令系统

> P2 | src/commands/ 模块文档

## 模块职责

**Commands 模块** 实现 100+ 内置 CLI 命令，覆盖会话管理、配置、调试、集成、工具调用等全方面功能。每个命令独立文件/目录，支持动态加载和插件扩展。

---

## 成员列表（按功能分类）

### 会话管理

| 命令 | 职责 |
|------|------|
| `session/` | 会话查询和管理 |
| `resume/` | 恢复会话 |
| `clear/` | 清除上下文 |
| `rename/` | 重命名会话 |
| `rewind/` | 回滚会话 |
| `share/` | 分享会话 |
| `export/` | 导出会话 |
| `copy/` | 复制内容 |

### Agent 和任务

| 命令 | 职责 |
|------|------|
| `agents/` | Agent 管理 |
| `tasks/` | 任务管理 |
| `advisor.ts` | 顾问模式 |
| `bughunter/` | Bug 猎手 |
| `autofix-pr/` | 自动修复 PR |

### 配置和设置

| 命令 | 职责 |
|------|------|
| `config/` | 配置管理 |
| `theme/` | 主题设置 |
| `keybindings/` | 键位绑定 |
| `model/` | 模型选择 |
| `privacy-settings/` | 隐私设置 |
| `permissions/` | 权限管理 |
| `env/` | 环境变量 |

### 调试和诊断

| 命令 | 职责 |
|------|------|
| `doctor/` | 健康检查 |
| `debug-tool-call/` | 调试工具调用 |
| `stats/` | 统计信息 |
| `status/` | 状态查询 |
| `cost/` | 成本查询 |
| `usage/` | 使用情况 |
| `perf-issue/` | 性能问题诊断 |
| `heapdump/` | 堆转储 |

### Git 和代码

| 命令 | 职责 |
|------|------|
| `branch/` | 分支管理 |
| `diff/` | 差异比较 |
| `commit.ts` | 提交代码 |
| `commit-push-pr.ts` | 提交并推 PR |
| `review/` | 代码审查 |
| `pr_comments/` | PR 评论 |
| `issue/` | Issue 管理 |

### MCP 和集成

| 命令 | 职责 |
|------|------|
| `mcp/` | MCP 管理 |
| `bridge/` | 桥接管理 |
| `bridge-kick.ts` | 桥接启动 |
| `ide/` | IDE 集成 |
| `chrome/` | Chrome 集成 |
| `desktop/` | 桌面集成 |
| `mobile/` | 移动集成 |

### 技能和插件

| 命令 | 职责 |
|------|------|
| `skills/` | 技能管理 |
| `plugin/` | 插件管理 |
| `reload-plugins/` | 重载插件 |
| `install-github-app/` | 安装 GitHub App |
| `install-slack-app/` | 安装 Slack App |

### 上下文和记忆

| 命令 | 职责 |
|------|------|
| `context/` | 上下文管理 |
| `memory/` | 记忆管理 |
| `compact/` | 上下文压缩 |
| `add-dir/` | 添加目录 |
| `files/` | 文件管理 |

### 输出和显示

| 命令 | 职责 |
|------|------|
| `color/` | 颜色设置 |
| `output-style/` | 输出样式 |
| `summary/` | 摘要生成 |
| `brief.ts` | 简报 |
| `ctx_viz/` | 上下文可视化 |

### 模式和功能

| 命令 | 职责 |
|------|------|
| `fast/` | 快速模式 |
| `plan/` | 计划模式 |
| `passes/` | Passes 管理 |
| `vim/` | Vim 模式 |
| `voice/` | 语音功能 |
| `sandbox-toggle/` | 沙箱切换 |

### 账户和认证

| 命令 | 职责 |
|------|------|
| `login/` | 登录 |
| `logout/` | 登出 |
| `oauth-refresh/` | OAuth 刷新 |

### 更新和反馈

| 命令 | 职责 |
|------|------|
| `upgrade/` | 升级检查 |
| `feedback/` | 反馈提交 |
| `release-notes/` | 发布说明 |
| `onboarding/` | 新手引导 |

### 其他命令

| 命令 | 职责 |
|------|------|
| `help/` | 帮助信息 |
| `exit/` | 退出 |
| `thinkback/` | 回顾思考 |
| `thinkback-play/` | 思考回放 |
| `teleport/` | 瞬移功能 |
| `sticky/` | 粘性模式 |
| `effort/` | 工作量评估 |
| `btw/` | 顺便提及 |
| `good-claude/` | 好评反馈 |
| `stickers/` | 贴纸功能 |
| `tag/` | 标签管理 |
| `remote-env/` | 远程环境 |
| `remote-setup/` | 远程设置 |
| `reset-limits/` | 重置限制 |
| `break-cache/` | 破坏缓存 |
| `mock-limits/` | 模拟限制 |
| `hooks/` | 钩子管理 |
| `terminalSetup/` | 终端设置 |
| `extra-usage/` | 额外使用 |
| `ant-trace/` | 追踪 |
| `backfill-sessions/` | 回填会话 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/tools/ (工具调用)
  - src/services/ (服务层)
  - src/cli/ (CLI 框架)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/cli/handlers/ (命令处理器)
  - 用户直接调用

[HERE] 位置:
  - src/commands/ 位于源码核心层
  - 每个命令独立文件，支持动态加载
```

---

## 命令注册机制

```typescript
// 命令注册模式
interface Command {
  name: string;
  aliases?: string[];
  description: string;
  handler: (args: Args) => Promise<void>;
  options?: Option[];
}
```

---

## 架构特点

1. **扁平结构** — 每个命令独立文件/目录，便于查找
2. **动态加载** — 支持插件扩展新命令
3. **统一接口** — 所有命令遵循相同处理模式
4. **帮助系统** — 自动生成帮助文档

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
