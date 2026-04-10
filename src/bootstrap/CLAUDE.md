# Bootstrap 模块 · 引导初始化

> P2 | src/bootstrap/ 模块文档

## 模块职责

**Bootstrap 模块** 提供应用引导和初始化状态管理，包括会话 ID、项目根目录、Git 状态、OpenTelemetry 配置等。是应用启动时的第一个初始化层。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `state.ts` | 引导状态管理 | ~1760 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - @opentelemetry/api (遥测)
  - @anthropic-ai/sdk (API 类型)
  - src/utils/ (工具函数)
  - src/types/ (类型定义)

[TO] 被消费于:
  - src/setup.ts (应用设置)
  - src/entrypoints/cli.tsx (入口点)
  - src/services/ (服务层)
  - src/utils/ (工具函数)

[HERE] 位置:
  - src/bootstrap/ 位于最底层
  - 是应用初始化的第一行代码
```

---

## 核心功能

### 会话管理
- `getSessionId()` — 获取会话 ID
- `switchSession()` — 切换会话
- `setProjectRoot()` — 设置项目根目录
- `getProjectRoot()` — 获取项目根目录

### Git 状态
- `getCachedBranch()` — 缓存分支名
- `getCachedHead()` — 缓存 HEAD
- `getCachedRemoteUrl()` — 缓存远程 URL

### 遥测配置
- OpenTelemetry TracerProvider
- OpenTelemetry MeterProvider
- OpenTelemetry LoggerProvider

### 状态信号
- `createSignal()` — 创建信号
- 异步状态管理
- 状态变更通知

---

## 初始化流程

```
1. 设置会话 ID
2. 检测项目根目录
3. 初始化 Git 缓存
4. 配置 OpenTelemetry
5. 注册清理回调
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
