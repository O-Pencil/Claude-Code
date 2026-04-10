# Tasks 模块 · 任务管理系统

> P2 | src/tasks/ 模块文档

## 模块职责

**Tasks 模块** 实现任务调度和执行系统，包括本地 Agent 任务、Shell 任务、远程任务、团队协作任务等。负责任务生命周期管理、状态跟踪、并发控制。

---

## 成员列表

### 核心任务类型

| 文件/目录 | 职责 | 行数 |
|-----------|------|------|
| `LocalMainSessionTask.ts` | 本地主会话任务 | ~380 行 |
| `LocalAgentTask/` | 本地 Agent 任务 | |
| `LocalShellTask/` | 本地 Shell 任务 | |
| `RemoteAgentTask/` | 远程 Agent 任务 | |
| `InProcessTeammateTask/` | 进程中队友任务 | |
| `DreamTask/` | 梦想模式任务 | |

### 任务管理

| 文件 | 职责 | 行数 |
|------|------|------|
| `stopTask.ts` | 任务停止逻辑 | ~70 行 |
| `pillLabel.ts` | 任务标签显示 | ~70 行 |
| `types.ts` | 任务类型定义 | ~40 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/tools/ (工具执行)
  - src/services/ (服务层)
  - src/types/ (类型定义)
  - src/state/ (状态管理)

[TO] 被消费于:
  - src/coordinator/ (协调器)
  - src/commands/tasks/ (任务命令)
  - src/tools/Task*Tool/ (任务工具)

[HERE] 位置:
  - src/tasks/ 位于核心执行层
  - 连接协调器和工具执行
```

---

## 任务类型详解

### LocalMainSessionTask
- 主会话任务，管理用户交互循环
- 处理消息历史和上下文
- 协调工具调用和响应生成

### LocalAgentTask
- 本地 Agent 执行任务
- 支持多 Agent 并发
- 管理 Agent 状态和通信

### LocalShellTask
- Shell 命令执行任务
- 进程管理和输出捕获
- 前台/后台任务切换

### RemoteAgentTask
- 远程 Agent 任务
- 支持远程开发和云执行
- 网络通信和同步

### InProcessTeammateTask
- 队友协作任务
- 支持多用户协作会话
- 状态同步和权限管理

### DreamTask
- 梦想模式任务
- 后台异步执行
- 长时间运行任务支持

---

## 任务生命周期

```
创建 → 排队 → 执行中 → (可选：暂停/恢复) → 完成/失败
         ↓
       取消/停止
```

---

## 关键功能

1. **并发控制** — 管理多任务并行执行
2. **状态跟踪** — 实时更新任务状态
3. **资源管理** — CPU/内存/网络资源分配
4. **错误恢复** — 任务失败重试和回滚
5. **进度报告** — 向用户报告执行进度

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
