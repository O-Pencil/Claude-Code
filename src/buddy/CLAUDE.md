# Buddy 模块 · 伴侣系统

> P2 | src/buddy/ 模块文档

## 模块职责

**Buddy 模块** 实现伴侣系统，包括伴侣角色、精灵动画、提示系统、通知等。提供友好的用户交互体验。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `companion.ts` | 伴侣核心逻辑 | ~200 行 |
| `CompanionSprite.tsx` | 伴侣精灵组件 | ~150 行 |
| `sprites.ts` | 精灵定义 | ~100 行 |
| `prompt.ts` | 伴侣提示 | ~80 行 |
| `types.ts` | 类型定义 | ~50 行 |
| `useBuddyNotification.tsx` | 伴侣通知钩子 | ~100 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (组件)
  - src/components/ (UI 组件)
  - src/hooks/ (钩子)

[TO] 被消费于:
  - src/components/ (UI 展示)
  - src/entrypoints/cli.tsx (入口点)

[HERE] 位置:
  - src/buddy/ 位于用户交互层
  - 提供友好的伴侣体验
```

---

## 核心功能

### 伴侣逻辑 (`companion.ts`)
- 伴侣状态管理
- 伴侣行为决策
- 伴侣响应生成

### 精灵系统 (`sprites.ts`, `CompanionSprite.tsx`)
- 精灵动画
- 表情状态
- 视觉反馈

### 通知系统 (`useBuddyNotification.tsx`)
- 伴侣通知
- 提示显示
- 交互反馈

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
