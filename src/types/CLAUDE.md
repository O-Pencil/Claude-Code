# Types 模块 · 类型定义

> P2 | src/types/ 模块文档

## 模块职责

**Types 模块** 定义全局 TypeScript 类型，包括命令、权限、插件、日志、ID、钩子等核心类型。提供类型安全和跨模块共享的类型契约。

---

## 成员列表

### 核心类型文件

| 文件 | 职责 | 行数 |
|------|------|------|
| `permissions.ts` | 权限系统类型 | ~320 行 |
| `plugin.ts` | 插件系统类型 | ~280 行 |
| `textInputTypes.ts` | 文本输入类型 | ~290 行 |
| `logs.ts` | 日志类型 | ~280 行 |
| `hooks.ts` | 钩子类型 | ~230 行 |
| `command.ts` | 命令类型 | ~190 行 |
| `ids.ts` | ID 类型定义 | ~30 行 |

### 生成代码

| 目录 | 职责 |
|------|------|
| `generated/` | 自动生成的类型（Protobuf/API） |
| `generated/events_mono/` | 事件类型（单体） |
| `generated/google/protobuf/` | Protobuf 类型 |

---

## 依赖关系

```
[FROM] 依赖:
  - 外部 SDK (@anthropic-ai/sdk)
  - Zod (运行时类型验证)

[TO] 被消费于:
  - 全项目所有模块
  - src/tools/, src/services/, src/components/

[HERE] 位置:
  - src/types/ 位于基础层
  - 被所有上层模块依赖
```

---

## 类型分类

### 权限类型 (`permissions.ts`)
- `PermissionType` — 权限类型枚举
- `PermissionRequest` — 权限请求结构
- `PermissionState` — 权限状态
- `PermissionCallback` — 权限回调

### 插件类型 (`plugin.ts`)
- `PluginDefinition` — 插件定义
- `PluginContext` — 插件上下文
- `PluginAPI` — 插件 API
- `PluginLifecycle` — 插件生命周期

### 输入类型 (`textInputTypes.ts`)
- `TextInputConfig` — 输入配置
- `InputValidation` — 输入验证
- `InputTransform` — 输入转换

### 日志类型 (`logs.ts`)
- `LogEntry` — 日志条目
- `LogLevel` — 日志级别
- `LogContext` — 日志上下文

### 钩子类型 (`hooks.ts`)
- `HookDefinition` — 钩子定义
- `HookContext` — 钩子上下文
- `HookRegistry` — 钩子注册表

### 命令类型 (`command.ts`)
- `CommandDefinition` — 命令定义
- `CommandArgs` — 命令参数
- `CommandResult` — 命令结果

### ID 类型 (`ids.ts`)
- `AgentId` — Agent ID
- `SessionId` — 会话 ID
- `TaskId` — 任务 ID
- `ToolId` — 工具 ID

---

## 生成代码

`generated/` 目录包含自动生成的类型：

```
generated/
├── events_mono/       # 事件类型（单体仓库）
│   ├── claude_code/   # Claude Code 事件
│   ├── common/        # 通用事件
│   └── growthbook/    # GrowthBook 事件
└── google/protobuf/   # Protobuf 类型
```

---

## 类型设计原则

1. **严格模式** — 启用严格 TypeScript 检查
2. **运行时验证** — 使用 Zod 进行运行时类型检查
3. **不可变优先** — 使用 `readonly` 和 `as const`
4. **类型推导** — 优先让编译器推导类型
5. **文档化** — 复杂类型附带 JSDoc 注释

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
