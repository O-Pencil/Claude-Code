# Remote 模块 · 远程会话管理

> P2 | src/remote/ 模块文档

## 模块职责

**Remote 模块** 实现远程会话管理，包括远程权限桥接、会话管理器、SDK 消息适配、WebSocket 通信等。支持远程开发和云执行模式。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `RemoteSessionManager.ts` | 远程会话管理器 | ~300 行 |
| `SessionsWebSocket.ts` | WebSocket 通信 | ~200 行 |
| `remotePermissionBridge.ts` | 远程权限桥接 | ~150 行 |
| `sdkMessageAdapter.ts` | SDK 消息适配 | ~100 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/tasks/RemoteAgentTask/ (远程任务)
  - src/services/api/ (API 服务)
  - src/types/ (类型定义)
  - WebSocket (通信协议)

[TO] 被消费于:
  - src/entrypoints/cli.tsx (入口点)
  - src/tasks/RemoteAgentTask/ (远程任务)
  - src/bridge/ (桥接层)

[HERE] 位置:
  - src/remote/ 位于远程通信层
  - 连接本地和远程执行环境
```

---

## 核心功能

### 远程会话管理 (`RemoteSessionManager.ts`)
- 创建远程会话
- 会话状态跟踪
- 会话生命周期管理

### WebSocket 通信 (`SessionsWebSocket.ts`)
- WebSocket 连接管理
- 消息发送/接收
- 心跳和重连

### 权限桥接 (`remotePermissionBridge.ts`)
- 远程权限请求
- 权限审批转发
- 权限状态同步

### 消息适配 (`sdkMessageAdapter.ts`)
- SDK 消息格式转换
- 协议适配
- 错误处理

---

## 远程模式

```
本地 CLI ←→ WebSocket ←→ 远程服务器
    ↓                        ↓
  用户输入                代码执行
    ↓                        ↓
  结果显示 ←←←←←←←←←  执行结果
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
