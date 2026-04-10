# Query 模块 · 查询配置

> P2 | src/query/ 模块文档

## 模块职责

**Query 模块** 提供查询相关配置和工具，包括查询配置、依赖管理、停止钩子、Token 预算等。支持 query.ts 核心查询逻辑。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `config.ts` | 查询配置 | ~100 行 |
| `deps.ts` | 依赖管理 | ~50 行 |
| `stopHooks.ts` | 停止钩子 | ~80 行 |
| `tokenBudget.ts` | Token 预算 | ~100 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/services/api/ (API 服务)
  - src/utils/ (工具函数)
  - src/types/ (类型定义)

[TO] 被消费于:
  - src/query.ts (查询核心)
  - src/QueryEngine.ts (查询引擎)
  - src/tools/ (工具调用)

[HERE] 位置:
  - src/query/ 位于查询配置层
  - 支持查询核心逻辑
```

---

## 核心功能

### 查询配置 (`config.ts`)
- 查询参数配置
- 模型设置
- 超时配置

### Token 预算 (`tokenBudget.ts`)
- Token 预算管理
- 预算检查
- 预算警告

### 停止钩子 (`stopHooks.ts`)
- 停止条件注册
- 停止条件检查
- 提前终止

### 依赖管理 (`deps.ts`)
- 依赖注入
- 依赖解析

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
