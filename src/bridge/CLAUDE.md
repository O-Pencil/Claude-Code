# Bridge 模块 · VSCode 桥接层

> P2 | src/bridge/ 模块文档

## 模块职责

**Bridge 模块** 提供 Claude Code 与 VSCode 扩展之间的桥接功能，包括会话管理、消息传递、权限回调、UI 集成等。

---

## 成员列表

### 核心文件

| 文件 | 职责 | 行数 |
|------|------|------|
| `bridgeMain.ts` | 桥接主入口，初始化逻辑 | ~2900 行 |
| `replBridge.ts` | REPL 桥接核心实现 | ~2600 行 |
| `remoteBridgeCore.ts` | 远程桥接核心 | ~950 行 |
| `initReplBridge.ts` | REPL 桥接初始化 | ~580 行 |
| `sessionRunner.ts` | 会话运行器 | ~440 行 |

### API 和配置

| 文件 | 职责 |
|------|------|
| `bridgeApi.ts` | 桥接 API 接口定义 |
| `bridgeConfig.ts` | 桥接配置管理 |
| `codeSessionApi.ts` | 代码会话 API |
| `types.ts` | 类型定义 |

### 消息和传输

| 文件 | 职责 |
|------|------|
| `bridgeMessaging.ts` | 消息传递机制 |
| `replBridgeTransport.ts` | REPL 传输层 |
| `inboundMessages.ts` | 入站消息处理 |
| `inboundAttachments.ts` | 入站附件处理 |

### 会话管理

| 文件 | 职责 |
|------|------|
| `createSession.ts` | 会话创建逻辑 |
| `sessionIdCompat.ts` | 会话 ID 兼容性处理 |
| `workSecret.ts` | 工作密钥管理 |

### UI 和状态

| 文件 | 职责 |
|------|------|
| `bridgeUI.ts` | UI 集成 |
| `bridgeStatusUtil.ts` | 状态工具 |
| `bridgePointer.ts` | 指针管理 |

### 权限和安全

| 文件 | 职责 |
|------|------|
| `bridgePermissionCallbacks.ts` | 权限回调 |
| `trustedDevice.ts` | 可信设备管理 |
| `jwtUtils.ts` | JWT 工具 |

### 调试和工具

| 文件 | 职责 |
|------|------|
| `bridgeDebug.ts` | 调试工具 |
| `debugUtils.ts` | 调试辅助 |
| `envLessBridgeConfig.ts` | 无环境配置 |
| `pollConfig.ts` | 轮询配置 |
| `pollConfigDefaults.ts` | 轮询默认值 |
| `flushGate.ts` | 刷新门控 |
| `capacityWake.ts` | 容量唤醒 |
| `bridgeEnabled.ts` | 桥接启用检查 |

---

## 依赖关系

```
[FROM] 依赖:
  - VSCode Extension API (通过桥接协议)
  - src/types/ (类型定义)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/entrypoints/ (入口点)
  - src/cli/ (命令行接口)
  - VSCode 扩展宿主

[HERE] 位置:
  - src/bridge/ 位于源码根目录
  - 是 VSCode 集成的核心入口层
```

---

## 关键导出

- `bridgeMain.ts` → 桥接初始化主函数
- `bridgeApi.ts` → 桥接 API 接口
- `replBridge.ts` → REPL 桥接类
- `createSession.ts` → 会话创建函数
- `types.ts` → 桥接相关类型

---

## 架构模式

1. **消息传递** — 使用异步消息队列在 VSCode 和 CLI 之间通信
2. **会话隔离** — 每个工作区/会话独立管理状态
3. **权限代理** — 权限请求转发到 VSCode UI 处理
4. **远程支持** — 支持远程开发和本地代理模式

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
