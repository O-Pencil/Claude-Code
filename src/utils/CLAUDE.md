# Utils 模块 · 工具函数库

> P2 | src/utils/ 模块文档

## 模块职责

**Utils 模块** 提供 300+ 通用工具函数，覆盖字符串处理、文件操作、网络请求、类型验证、日志记录、测试辅助等。是全项目共享的基础工具层。

---

## 成员列表（按功能分类）

### 核心工具

| 文件 | 职责 |
|------|------|
| `api.ts` | API 请求封装 |
| `debug.ts` | 调试工具 |
| `errors.ts` | 错误处理 |
| `log.ts` | 日志记录 |
| `sleep.ts` | 延迟工具 |
| `uuid.ts` | UUID 生成 |

### 字符串和文本

| 文件 | 职责 |
|------|------|
| `format.ts` | 格式化函数 |
| `truncate.ts` | 截断函数 |
| `words.ts` | 单词处理 |
| `xml.ts` | XML 处理 |
| `yaml.ts` | YAML 处理 |
| `textHighlighting.ts` | 文本高亮 |

### 文件和路径

| 文件 | 职责 |
|------|------|
| `file.ts` | 文件操作 |
| `paths.ts` | 路径处理 |
| `xdg.ts` | XDG 目录规范 |
| `windowsPaths.ts` | Windows 路径 |
| `cachePaths.ts` | 缓存路径 |
| `tempfile.ts` | 临时文件 |

### Bash 和 Shell

| 文件/目录 | 职责 |
|-----------|------|
| `bash/` | Bash 工具（AST 解析、命令分割） |
| `shell.ts` | Shell 抽象 |
| `terminal.ts` | 终端处理 |
| `tmuxSocket.ts` | Tmux 套接字 |
| `appleTerminalBackup.ts` | Apple Terminal 备份 |
| `asciicast.ts` | Asciicast 录制 |

### 网络和 HTTP

| 文件 | 职责 |
|------|------|
| `http.ts` | HTTP 工具 |
| `fetch.ts` | Fetch 封装 |
| `apiPreconnect.ts` | API 预连接 |
| `browser.ts` | 浏览器工具 |
| `userAgent.ts` | User-Agent 处理 |

### 认证和安全

| 文件 | 职责 |
|------|------|
| `auth.ts` | 认证逻辑 |
| `authPortable.ts` | 便携式认证 |
| `authFileDescriptor.ts` | 认证文件描述符 |
| `jwt.ts` | JWT 工具 |
| `secretStorage.ts` | 密钥存储 |
| `secureStorage.ts` | 安全存储 |

### Git 和版本控制

| 文件/目录 | 职责 |
|-----------|------|
| `git/` | Git 操作 |
| `github/` | GitHub API |
| `worktree.ts` | Git Worktree |
| `worktreeModeEnabled.ts` | Worktree 模式检查 |

### 类型和验证

| 文件 | 职责 |
|------|------|
| `zodToJsonSchema.ts` | Zod 转 JSON Schema |
| `typeGuards.ts` | 类型守卫 |
| `array.ts` | 数组工具 |
| `object.ts` | 对象工具 |
| `promise.ts` | Promise 工具 |
| `withResolvers.ts` | Promise 解决器 |

### 工具和命令

| 文件 | 职责 |
|------|------|
| `which.ts` | 命令查找 |
| `binaryCheck.ts` | 二进制检查 |
| `toolSchemaCache.ts` | 工具 Schema 缓存 |
| `toolSearch.ts` | 工具搜索 |
| `toolPool.ts` | 工具池 |
| `toolErrors.ts` | 工具错误 |

### 状态和管理

| 文件 | 职责 |
|------|------|
| `state.ts` | 状态管理 |
| `cleanupRegistry.ts` | 清理注册表 |
| `activityManager.ts` | 活动管理 |
| `abortController.ts` | AbortController 工具 |

### 配置和环境

| 文件 | 职责 |
|------|------|
| `envUtils.ts` | 环境变量工具 |
| `settings.ts` | 设置工具 |
| `bundledMode.ts` | 捆绑模式 |
| `betas.ts` | Beta 功能 |

### 性能和资源

| 文件 | 职责 |
|------|------|
| `tokens.ts` | Token 计算 |
| `tokenBudget.ts` | Token 预算 |
| `resourceLimits.ts` | 资源限制 |
| `timeouts.ts` | 超时处理 |

### 测试和模拟

| 文件/目录 | 职责 |
|-----------|------|
| `testing/` | 测试工具 |
| `mocks/` | 模拟数据 |
| `fixtures/` | 测试夹具 |

### UI 和渲染

| 文件 | 职责 |
|------|------|
| `ansiToPng.ts` | ANSI 转 PNG |
| `ansiToSvg.ts` | ANSI 转 SVG |
| `theme.ts` | 主题处理 |
| `treeify.ts` | 树形展示 |

### 后台任务

| 文件/目录 | 职责 |
|-----------|------|
| `background/` | 后台任务 |
| `backgroundHousekeeping.ts` | 后台清理 |
| `preventSleep.ts` | 防止休眠 |

### 特定功能

| 文件/目录 | 职责 |
|-----------|------|
| `memory/` | 记忆工具 |
| `mcp/` | MCP 工具 |
| `permissions/` | 权限工具 |
| `plugins/` | 插件工具 |
| `skills/` | 技能工具 |
| `task/` | 任务工具 |
| `telemetry/` | 遥测工具 |
| `suggestions/` | 建议工具 |
| `todo/` | TODO 工具 |
| `ultraplan/` | UltraPlan 工具 |
| `swarm/` | Swarm 工具 |
| `teleport/` | Teleport 工具 |

### 其他工具

| 文件 | 职责 |
|------|------|
| `bufferedWriter.ts` | 缓冲写入器 |
| `CircularBuffer.ts` | 环形缓冲区 |
| `deepLink.ts` | 深度链接 |
| `dxt.ts` | DXT 工具 |
| `filePersistence.ts` | 文件持久化 |
| `hooks.ts` | 钩子工具 |
| `messages.ts` | 消息工具 |
| `model.ts` | 模型工具 |
| `nativeInstaller.ts` | 原生安装器 |
| `powershell.ts` | PowerShell 工具 |
| `processUserInput.ts` | 用户输入处理 |
| `sandbox.ts` | 沙箱工具 |
| `streamlinedTransform.ts` | 流式转换 |
| `unaryLogging.ts` | 一元日志 |
| `undercover.ts` | 卧底模式 |
| `user.ts` | 用户工具 |
| `warningHandler.ts` | 警告处理 |
| `claudeCodeHints.ts` | Claude Code 提示 |
| `claudeInChrome.ts` | Chrome 集成 |
| `codeIndexing.ts` | 代码索引 |
| `computerUse.ts` | 电脑使用 |
| `diagnostics.ts` | 诊断工具 |
| `envUtils.ts` | 环境工具 |
| `format.ts` | 格式工具 |
| `streamJsonStdoutGuard.ts` | JSON 输出保护 |

---

## 依赖关系

```
[FROM] 依赖:
  - Node.js 内置模块 (fs, path, crypto, os 等)
  - 第三方库 (zod, axios, etc.)

[TO] 被消费于:
  - 全项目所有模块
  - src/tools/, src/services/, src/commands/

[HERE] 位置:
  - src/utils/ 位于基础层
  - 被所有上层模块依赖
```

---

## 工具函数设计规范

```typescript
// 纯函数优先
export function formatString(input: string): string { }

// 错误处理
export function safeParse(json: string): Result<T, Error> { }

// 异步工具
export async function fetchWithRetry(url: string): Promise<Response> { }
```

---

## 架构特点

1. **纯函数优先** — 大部分工具函数是无副作用的纯函数
2. **类型安全** — 完整的 TypeScript 类型标注
3. **错误处理** — 统一的错误处理和返回模式
4. **可测试** — 设计为易于单元测试
5. **性能优化** — 关键路径上的函数经过性能优化

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
