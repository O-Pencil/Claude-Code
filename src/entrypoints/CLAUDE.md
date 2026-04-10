# Entrypoints 模块 · 应用入口

> P2 | src/entrypoints/ 模块文档

## 模块职责

**Entrypoints 模块** 提供应用入口点，包括 CLI 启动、MCP 服务、SDK 导出等。是应用启动和初始化的入口层。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `cli.tsx` | CLI 入口点 | ~300 行 |
| `init.ts` | 初始化逻辑 | ~100 行 |
| `mcp.ts` | MCP 服务入口 | ~80 行 |
| `agentSdkTypes.ts` | Agent SDK 类型 | ~150 行 |
| `sandboxTypes.ts` | 沙箱类型 | ~50 行 |
| `sdk/` | SDK 导出 | |

---

## 依赖关系

```
[FROM] 依赖:
  - src/setup.ts (应用设置)
  - src/bridge/ (桥接层)
  - src/services/ (服务层)

[TO] 被消费于:
  - dist/cli.js (构建输出)
  - 外部调用者

[HERE] 位置:
  - src/entrypoints/ 位于应用最外层
  - 是应用启动的第一行代码
```

---

## 入口点详解

### CLI (`cli.tsx`)
- 检查启动标志
- 初始化应用
- 启动 REPL 或执行命令
- 处理特殊模式（bare、remote 等）

### MCP (`mcp.ts`)
- MCP 服务器启动
- MCP 工具注册
- MCP 资源暴露

### SDK (`sdk/`)
- Agent SDK 导出
- 类型定义
- 工具函数

---

## 启动流程

```
1. cli.tsx 执行
2. 检查特殊标志 (--bare, --remote 等)
3. 调用 setup.ts 初始化
4. 启动 Bridge (VSCode 集成)
5. 进入 REPL 循环或执行命令
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
