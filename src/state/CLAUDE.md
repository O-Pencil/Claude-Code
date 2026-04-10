# State 模块 · 状态管理

> P2 | src/state/ 模块文档

## 模块职责

**State 模块** 提供应用状态管理，包括 AppState 定义、状态存储、选择器、变更通知等。使用 React Context 和外部存储模式实现跨组件状态共享。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `AppState.tsx` | 状态提供者组件 | ~590 行 |
| `AppStateStore.ts` | 状态存储定义 | ~540 行 |
| `onChangeAppState.ts` | 状态变更监听 | ~150 行 |
| `selectors.ts` | 状态选择器 | ~55 行 |
| `store.ts` | 存储创建工具 | ~20 行 |
| `teammateViewHelpers.ts` | 队友视图辅助 | ~110 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (Context, useSyncExternalStore)
  - src/utils/ (工具函数)
  - src/types/ (类型定义)

[TO] 被消费于:
  - src/components/App.tsx
  - src/hooks/ (各种钩子)
  - src/entrypoints/cli.tsx

[HERE] 位置:
  - src/state/ 位于核心状态层
  - 被 UI 层和业务层广泛依赖
```

---

## 关键导出

- `AppState` — 应用状态类型定义
- `AppStateProvider` — 状态提供者组件
- `onChangeAppState` — 状态变更订阅
- `selectors` — 状态选择器集合

---

## 状态结构

```typescript
interface AppState {
  messages: Message[];
  tools: Tool[];
  settings: Settings;
  permissions: PermissionState;
  // ... 更多状态字段
}
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
