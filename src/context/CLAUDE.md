# Context 模块 · React 上下文

> P2 | src/context/ 模块文档

## 模块职责

**Context 模块** 提供 React Context 提供者，包括邮箱、通知、覆盖层、统计、语音等。实现跨组件树的状态共享和依赖注入。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `mailbox.tsx` | 邮箱上下文（消息队列） | ~40 行 |
| `notifications.tsx` | 通知上下文 | ~100 行 |
| `overlayContext.tsx` | 覆盖层上下文 | ~150 行 |
| `promptOverlayContext.tsx` | 提示覆盖层上下文 | ~100 行 |
| `modalContext.tsx` | 模态框上下文 | ~100 行 |
| `QueuedMessageContext.tsx` | 队列消息上下文 | ~80 行 |
| `stats.tsx` | 统计上下文 | ~100 行 |
| `fpsMetrics.tsx` | FPS 指标上下文 | ~80 行 |
| `voice.tsx` | 语音上下文（Ant 专用） | ~200 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (createContext, useContext, Provider)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/components/App.tsx
  - src/components/ (各种 UI 组件)
  - src/hooks/ (钩子)

[HERE] 位置:
  - src/context/ 位于 UI 基础层
  - 被组件树广泛使用
```

---

## 上下文设计模式

```typescript
// 创建上下文
const MyContext = createContext<MyType | undefined>(undefined);

// 提供者组件
export function MyProvider({ children }) {
  const value = useMyContextValue();
  return (
    <MyContext.Provider value={value}>
      {children}
    </MyContext.Provider>
  );
}

// 消费钩子
export function useMyContext() {
  const context = useContext(MyContext);
  if (!context) {
    throw new Error('useMyContext must be used within MyProvider');
  }
  return context;
}
```

---

## 关键上下文

### MailboxContext
- 消息队列和投递
- 异步消息处理

### NotificationsContext
- 通知管理
- 通知显示和清除

### OverlayContext
- 覆盖层管理
- 模态框控制

### StatsContext
- 性能统计
- 指标收集

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
