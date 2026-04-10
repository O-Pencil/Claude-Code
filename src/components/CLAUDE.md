# Components 模块 · UI 组件库

> P2 | src/components/ 模块文档

## 模块职责

**Components 模块** 提供 140+ React/Ink UI 组件，包括对话框、权限请求、进度显示、消息渲染、设置界面等。支持终端 UI（Ink）和桌面 UI（React）双渲染模式。

---

## 成员列表（按功能分类）

### 核心组件

| 组件 | 职责 |
|------|------|
| `App.tsx` | 应用根组件 |
| `design-system/` | 设计系统基础组件 |
| `ui/` | 通用 UI 组件 |
| `shell/` | Shell 界面组件 |

### Agent 和任务

| 组件 | 职责 |
|------|------|
| `agents/` | Agent 相关组件 |
| `AgentProgressLine.tsx` | Agent 进度线 |
| `CoordinatorAgentStatus.tsx` | 协调器状态 |
| `tasks/` | 任务 UI |

### 权限和安全

| 组件 | 职责 |
|------|------|
| `permissions/` | 权限请求组件 |
| `AskUserQuestionPermissionRequest/` | 提问权限 |
| `BashPermissionRequest/` | Bash 权限 |
| `FilePermissionDialog/` | 文件权限 |
| `FilesystemPermissionRequest/` | 文件系统权限 |
| `SkillPermissionRequest/` | 技能权限 |
| `WebFetchPermissionRequest/` | 网页访问权限 |
| `ComputerUseApproval/` | 电脑使用审批 |
| `BypassPermissionsModeDialog/` | 绕过权限模式 |

### 权限请求类型

| 组件 | 职责 |
|------|------|
| `EnterPlanModePermissionRequest/` | 计划模式权限 |
| `ExitPlanModePermissionRequest/` | 退出计划模式权限 |
| `FileEditPermissionRequest/` | 文件编辑权限 |
| `FileWritePermissionRequest/` | 文件写入权限 |
| `NotebookEditPermissionRequest/` | Notebook 编辑权限 |
| `PowerShellPermissionRequest/` | PowerShell 权限 |
| `SedEditPermissionRequest/` | Sed 编辑权限 |

### 消息和结果

| 组件 | 职责 |
|------|------|
| `messages/` | 消息组件 |
| `UserToolResultMessage/` | 工具结果消息 |
| `FallbackToolUseErrorMessage.tsx` | 错误消息 |
| `FallbackToolUseRejectedMessage.tsx` | 拒绝消息 |

### 设置和配置

| 组件 | 职责 |
|------|------|
| `Settings/` | 设置界面 |
| `ManagedSettingsSecurityDialog/` | 托管设置安全 |
| `ApproveApiKey.tsx` | API 密钥审批 |
| `ConfigurableShortcutHint.tsx` | 快捷键提示 |
| `DevChannelsDialog.tsx` | 开发渠道 |
| `CostThresholdDialog.tsx` | 成本阈值 |

### MCP 集成

| 组件 | 职责 |
|------|------|
| `mcp/` | MCP 相关组件 |
| `mcp/utils/` | MCP 工具函数 |

### 记忆和上下文

| 组件 | 职责 |
|------|------|
| `memory/` | 记忆组件 |
| `ContextSuggestions.tsx` | 上下文建议 |
| `ContextVisualization.tsx` | 上下文可视化 |
| `CompactSummary.tsx` | 压缩摘要 |

### 帮助和提示

| 组件 | 职责 |
|------|------|
| `HelpV2/` | 帮助系统 |
| `ClaudeCodeHint/` | Claude Code 提示 |
| `Tips/` | 使用提示 |

### 差异和代码

| 组件 | 职责 |
|------|------|
| `diff/` | 差异显示 |
| `StructuredDiff/` | 结构化差异 |
| `HighlightedCode/` | 代码高亮 |

### 进度和状态

| 组件 | 职责 |
|------|------|
| `BashModeProgress.tsx` | Bash 模式进度 |
| `EffortIndicator.ts` | 工作量指示器 |
| `EffortCallout.tsx` | 工作量说明 |
| `FastIcon.tsx` | 快速模式图标 |
| `Spinner/` | 加载动画 |

### 对话和弹窗

| 组件 | 职责 |
|------|------|
| `BridgeDialog.tsx` | 桥接对话框 |
| `ExportDialog.tsx` | 导出对话框 |
| `TrustDialog/` | 信任对话框 |
| `AutoModeOptInDialog.tsx` | 自动模式选择 |
| `ChannelDowngradeDialog.tsx` | 渠道降级 |
| `AwsAuthStatusBox.tsx` | AWS 认证状态 |

### 更新和迁移

| 组件 | 职责 |
|------|------|
| `AutoUpdater.tsx` | 自动更新 |
| `AutoUpdaterWrapper.tsx` | 更新包装器 |
| `ExitFlow.tsx` | 退出流程 |
| `DesktopHandoff.tsx` | 桌面交接 |

### 集成和扩展

| 组件 | 职责 |
|------|------|
| `ConsoleOAuthFlow.tsx` | OAuth 流程 |
| `ClaudeInChromeOnboarding.tsx` | Chrome 集成引导 |
| `DesktopUpsell/` | 桌面推广 |
| `LspRecommendation/` | LSP 推荐 |
| `teams/` | 团队功能 |

### 开发和调试

| 组件 | 职责 |
|------|------|
| `DevBar.tsx` | 开发工具栏 |
| `DiagnosticsDisplay.tsx` | 诊断显示 |
| `Passes/` | Passes 显示 |

### 输入和表单

| 组件 | 职责 |
|------|------|
| `BaseTextInput.tsx` | 基础文本输入 |
| `CustomSelect/` | 自定义选择器 |
| `PromptInput/` | 提示输入 |
| `wizard/` | 向导组件 |

### 其他组件

| 组件 | 职责 |
|------|------|
| `LogoV2/` | Logo |
| `ClickableImageRef.tsx` | 可点击图像 |
| `CtrlOToExpand.tsx` | 展开提示 |
| `sandbox/` | 沙箱 UI |
| `skills/` | 技能 UI |
| `grove/` | Grove 集成 |
| `FeedbackSurvey/` | 反馈调查 |
| `ReleaseNotes.tsx` | 发布说明 |
| `UsageLimits.tsx` | 使用限制 |
| `VerboseHeader.tsx` | 详细头部 |
| `ThinkingIndicator.tsx` | 思考指示器 |
| `ResumeSessionBanner.tsx` | 恢复会话横幅 |

### 钩子

| 目录 | 职责 |
|------|------|
| `hooks/` | React 钩子 |

---

## 依赖关系

```
[FROM] 依赖:
  - React, Ink (UI 框架)
  - src/types/ (类型定义)
  - src/hooks/ (钩子)
  - src/state/ (状态管理)

[TO] 被消费于:
  - src/entrypoints/ (入口点)
  - src/bridge/bridgeUI.ts (桥接 UI)
  - src/ink/ (终端 UI)

[HERE] 位置:
  - src/components/ 位于 UI 层
  - 支持终端和桌面双模式渲染
```

---

## 架构特点

1. **双渲染模式** — Ink（终端）和 React（桌面）共享组件逻辑
2. **权限组件化** — 每种权限类型有独立组件
3. **设计系统** — 统一的设计语言和组件 API
4. **状态驱动** — 基于 AppState 的响应式更新

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
