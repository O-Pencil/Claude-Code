# Native-ts 模块 · 原生 TypeScript 绑定

> P2 | src/native-ts/ 模块文档

## 模块职责

**Native-ts 模块** 提供原生模块的 TypeScript 绑定，包括颜色差异、文件索引、yoga 布局等。封装底层原生功能供上层使用。

---

## 成员列表

| 目录 | 职责 |
|------|------|
| `color-diff/` | 颜色差异计算绑定 |
| `file-index/` | 文件索引绑定 |
| `yoga-layout/` | Yoga 布局引擎绑定 |

---

## 依赖关系

```
[FROM] 依赖:
  - 原生模块 (.node 文件)
  - Node.js FFI

[TO] 被消费于:
  - src/ink/ (终端 UI)
  - src/components/ (UI 组件)
  - src/utils/ (工具函数)

[HERE] 位置:
  - src/native-ts/ 位于原生绑定层
  - 连接 JS 和原生代码
```

---

## 绑定模块

### color-diff
- 颜色差异计算
- ANSI 颜色优化
- 终端颜色匹配

### file-index
- 文件索引构建
- 快速文件查找
- 文件系统缓存

### yoga-layout
- Flexbox 布局计算
- 节点测量
- 布局约束求解

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
