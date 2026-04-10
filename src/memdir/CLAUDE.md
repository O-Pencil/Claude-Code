# Memdir 模块 · 记忆目录管理

> P2 | src/memdir/ 模块文档

## 模块职责

**Memdir 模块** 管理会话记忆目录，包括记忆文件路径、记忆扫描、记忆年龄计算、团队记忆等。支持自动记忆提取和持久化。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `paths.ts` | 记忆目录路径管理 | ~280 行 |
| `memdir.ts` | 记忆目录核心逻辑 | ~200 行 |
| `memoryScan.ts` | 记忆扫描 | ~150 行 |
| `memoryAge.ts` | 记忆年龄计算 | ~100 行 |
| `memoryTypes.ts` | 记忆类型定义 | ~80 行 |
| `findRelevantMemories.ts` | 相关记忆查找 | ~120 行 |
| `teamMemPaths.ts` | 团队记忆路径 | ~60 行 |
| `teamMemPrompts.ts` | 团队记忆提示 | ~100 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/bootstrap/state.js (状态管理)
  - src/utils/ (工具函数)
  - src/utils/settings/ (设置管理)

[TO] 被消费于:
  - src/services/SessionMemory/
  - src/commands/memory/
  - src/utils/claudemd.ts

[HERE] 位置:
  - src/memdir/ 位于记忆管理层
  - 连接会话记忆和文件系统
```

---

## 关键功能

### 路径管理 (`paths.ts`)
- 全局记忆路径 (`~/.claude/CLAUDE.md`)
- 项目记忆路径 (`CLAUDE.md`, `.claude/CLAUDE.md`)
- 本地记忆路径 (`CLAUDE.local.md`)
- 团队记忆路径

### 记忆扫描 (`memoryScan.ts`)
- 扫描记忆文件
- 提取关键信息
- 建立记忆索引

### 记忆年龄 (`memoryAge.ts`)
- 计算记忆新鲜度
- 记忆过期判断
- 记忆优先级排序

### 记忆查找 (`findRelevantMemories.ts`)
- 基于上下文查找相关记忆
- 记忆相关性评分
- 记忆过滤

---

## 记忆层级

```
1. Managed Memory (/etc/claude-code/CLAUDE.md)
   └─ 全局管理指令

2. User Memory (~/.claude/CLAUDE.md)
   └─ 用户全局指令

3. Project Memory (CLAUDE.md, .claude/CLAUDE.md)
   └─ 项目级指令

4. Local Memory (CLAUDE.local.md)
   └─ 本地私有指令
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
