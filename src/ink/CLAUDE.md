# Ink 模块 · 终端 UI 渲染引擎

> P2 | src/ink/ 模块文档

## 模块职责

**Ink 模块** 提供终端 UI 渲染引擎，包括 ANSI 处理、布局计算、事件处理、组件渲染等。支持 React 风格的终端界面开发。

---

## 成员列表

### 核心渲染

| 文件 | 职责 |
|------|------|
| `ink.tsx` | Ink 渲染核心 |
| `render.ts` | 渲染函数 |
| `root.ts` | 根组件管理 |
| `instances.ts` | 实例管理 |
| `frame.ts` | 帧管理 |
| `log-update.ts` | 日志更新 |

### ANSI 和颜色

| 文件 | 职责 |
|------|------|
| `Ansi.tsx` | ANSI 处理 |
| `colorize.ts` | 颜色处理 |
| `constants.ts` | 终端常量 |

### 布局

| 文件 | 职责 |
|------|------|
| `layout/` | 布局计算 |
| `measure-element.ts` | 元素测量 |
| `measure-text.ts` | 文本测量 |
| `get-max-width.ts` | 最大宽度 |
| `line-width-cache.ts` | 行宽缓存 |

### 事件

| 文件 | 职责 |
|------|------|
| `events/` | 事件处理 |
| `focus.ts` | 焦点管理 |
| `hit-test.ts` | 命中测试 |

### 组件

| 文件 | 职责 |
|------|------|
| `components/` | 基础组件 |
| `dom.ts` | DOM 操作 |
| `bidi.ts` | 双向文本 |
| `clearTerminal.ts` | 清屏 |

### 钩子

| 文件 | 职责 |
|------|------|
| `hooks/` | React 钩子 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (组件模型)
  - yoga-layout (布局引擎)
  - ansi-escapes (ANSI 控制)

[TO] 被消费于:
  - src/ink.ts (公共导出)
  - src/components/ (UI 组件)
  - src/entrypoints/cli.tsx (入口点)

[HERE] 位置:
  - src/ink/ 位于终端 UI 层
  - 提供 React 风格的终端渲染
```

---

## 架构特点

1. **React 兼容** — 使用 React 组件模型
2. **Flexbox 布局** — 基于 yoga-layout 的 Flexbox
3. **增量渲染** — 只更新变化的部分
4. **ANSI 优化** — 高效的 ANSI 转义序列

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
