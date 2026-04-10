# Keybindings 模块 · 键位绑定系统

> P2 | src/keybindings/ 模块文档

## 模块职责

**Keybindings 模块** 实现键位绑定系统，包括键位解析、chord 支持（组合键）、上下文感知、用户自定义绑定等。提供灵活的键盘快捷键管理。

---

## 成员列表

### 核心文件

| 文件 | 职责 | 行数 |
|------|------|------|
| `KeybindingContext.tsx` | 键位上下文 | ~240 行 |
| `KeybindingProviderSetup.tsx` | 键位提供者设置 | ~150 行 |
| `resolver.ts` | 键位解析器 | ~200 行 |
| `parser.ts` | 键位解析 | ~150 行 |
| `match.ts` | 键位匹配 | ~120 行 |

### 加载和配置

| 文件 | 职责 |
|------|------|
| `loadUserBindings.ts` | 加载用户绑定 |
| `defaultBindings.ts` | 默认绑定 |
| `schema.ts` | 绑定 Schema |
| `validate.ts` | 绑定验证 |

### 格式和显示

| 文件 | 职责 |
|------|------|
| `shortcutFormat.ts` | 快捷键格式 |
| `useShortcutDisplay.ts` | 快捷键显示 |
| `template.ts` | 绑定模板 |

### 钩子

| 文件 | 职责 |
|------|------|
| `useKeybinding.ts` | 键位钩子 |

### 其他

| 文件 | 职责 |
|------|------|
| `reservedShortcuts.ts` | 保留快捷键 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (Context, Provider)
  - src/ink.js (终端 UI)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/hooks/useCommandKeybindings.tsx
  - src/components/ (UI 组件)
  - src/entrypoints/cli.tsx

[HERE] 位置:
  - src/keybindings/ 位于输入处理层
  - 连接键盘输入和命令执行
```

---

## 键位格式

```typescript
// 单键
"ctrl+c"
"shift+tab"
"enter"

// 组合键 (Chord)
"ctrl+k ctrl+s"
"ctrl+x ctrl+f"

// 上下文感知
{
  keys: "ctrl+enter",
  action: "command:submit",
  context: "prompt-focused"
}
```

---

## 键位解析流程

```
1. 键盘事件 → Key 对象
2. Key + Chord 状态 → 解析器
3. 解析器 → Action 名称
4. Action → 命令执行
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
