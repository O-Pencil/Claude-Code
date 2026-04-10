# Services 模块 · 核心服务层

> P2 | src/services/ 模块文档

## 模块职责

**Services 模块** 提供核心业务服务，包括 API 通信、MCP 集成、会话管理、遥测分析、速率限制、OAuth 认证、LSP 支持等。是工具层之上的业务逻辑抽象。

---

## 成员列表

### API 和通信

| 文件/目录 | 职责 |
|-----------|------|
| `api/` | API 客户端和请求封装 |
| `oauth/` | OAuth 认证流程 |
| `vcr.ts` | 请求录制/回放（测试用） |

### MCP 服务

| 文件/目录 | 职责 |
|-----------|------|
| `mcp/` | MCP 客户端和服务管理 |
| `mcpServerApproval.tsx` | MCP 服务器审批 UI |

### 会话和记忆

| 文件/目录 | 职责 |
|-----------|------|
| `SessionMemory/` | 会话记忆管理 |
| `teamMemorySync/` | 团队记忆同步 |
| `settingsSync/` | 设置同步 |
| `extractMemories/` | 记忆提取服务 |

### 速率限制

| 文件/目录 | 职责 |
|-----------|------|
| `policyLimits/` | 策略限制 |
| `claudeAiLimits.ts` | Claude AI 限制逻辑 |
| `claudeAiLimitsHook.ts` | 限制钩子 |
| `mockRateLimits.ts` | 模拟速率限制 |
| `rateLimitMessages.ts` | 限制提示消息 |
| `rateLimitMocking.ts` | 限制模拟 |

### 分析和遥测

| 文件/目录 | 职责 |
|-----------|------|
| `analytics/` | 分析服务 |
| `diagnosticTracking.ts` | 诊断跟踪 |
| `internalLogging.ts` | 内部日志 |

### 摘要服务

| 文件/目录 | 职责 |
|-----------|------|
| `AgentSummary/` | Agent 摘要 |
| `toolUseSummary/` | 工具使用摘要 |
| `awaySummary.ts` | 离开摘要 |
| `compact/` | 上下文压缩 |

### LSP 和代码

| 文件/目录 | 职责 |
|-----------|------|
| `lsp/` | 语言服务器协议服务 |
| `MagicDocs/` | 文档生成 |

### 插件系统

| 文件/目录 | 职责 |
|-----------|------|
| `plugins/` | 插件管理 |
| `autoDream/` | 自动梦想模式 |

### 工具和权限

| 文件/目录 | 职责 |
|-----------|------|
| `tools/` | 工具服务 |
| `PromptSuggestion/` | 提示建议 |
| `tips/` | 使用提示 |

### 语音功能

| 文件 | 职责 |
|------|------|
| `voice.ts` | 语音核心 |
| `voiceStreamSTT.ts` | 语音流识别 |
| `voiceKeyterms.ts` | 语音关键词 |

### 其他服务

| 文件 | 职责 |
|------|------|
| `notifier.ts` | 通知服务 |
| `preventSleep.ts` | 防止休眠 |
| `tokenEstimation.ts` | Token 估算 |
| `remoteManagedSettings/` | 远程托管设置 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/types/ (类型定义)
  - src/utils/ (工具函数)
  - 外部 API (Anthropic API, MCP Servers)

[TO] 被消费于:
  - src/tools/ (工具层)
  - src/commands/ (命令层)
  - src/tasks/ (任务系统)

[HERE] 位置:
  - src/services/ 位于源码核心层
  - 承上启下：服务层 → 工具层 → 命令层
```

---

## 关键服务

1. **API 服务** — 与 Anthropic API 通信，处理认证和请求
2. **MCP 服务** — Model Context Protocol 集成
3. **速率限制** — 管理 API 调用频率和配额
4. **会话记忆** — 跨会话持久化上下文
5. **LSP 服务** — 代码智能感知支持

---

## 架构模式

- **服务隔离** — 每个服务独立目录，职责单一
- **可测试设计** — 支持 VCR 录制/回放测试
- **错误处理** — 统一的错误传播和恢复机制
- **配置驱动** — 通过配置控制服务行为

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
