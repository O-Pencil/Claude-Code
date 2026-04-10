# Vim 模块 · Vim 模式支持

> P2 | src/vim/ 模块文档

## 模块职责

**Vim 模块** 实现 Vim 风格的编辑功能，包括动作（motions）、操作符（operators）、文本对象（text objects）、模式转换等。提供 Vim 用户熟悉的编辑体验。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `motions.ts` | Vim 动作（hjkl 等） | ~200 行 |
| `operators.ts` | Vim 操作符（d, c, y 等） | ~150 行 |
| `textObjects.ts` | 文本对象（iw, aw 等） | ~120 行 |
| `transitions.ts` | 模式转换 | ~100 行 |
| `types.ts` | 类型定义 | ~50 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/types/ (类型定义)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/commands/vim/ (Vim 命令)
  - src/components/PromptInput/ (输入组件)

[HERE] 位置:
  - src/vim/ 位于编辑模式层
  - 提供 Vim 风格编辑
```

---

## Vim 功能

### 动作 (Motions)
- `h/j/k/l` — 方向移动
- `w/b` — 单词移动
- `0/$` — 行首/行尾
- `gg/G` — 文件首/尾

### 操作符 (Operators)
- `d` — 删除
- `c` — 修改
- `y` — 复制
- `>`/`<` — 缩进

### 文本对象 (Text Objects)
- `iw/aw` — 单词
- `is/as` — 句子
- `ip/ap` — 段落
- `i"/a"` — 引号内

### 模式转换
- 正常模式 ↔ 插入模式
- 正常模式 ↔ 可视模式

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
