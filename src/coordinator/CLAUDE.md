# Coordinator 模块 · 协调器系统

> P2 | src/coordinator/ 模块文档

## 模块职责

**Coordinator 模块** 实现协调器模式配置，包括协调器模式切换、工具白名单、特性开关等。管理 Agent 协调行为和执行策略。

---

## 成员列表

| 文件 | 职责 | 行数 |
|------|------|------|
| `coordinatorMode.ts` | 协调器模式配置 | ~370 行 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/constants/tools.js (工具常量)
  - src/services/analytics/ (特性开关)
  - src/tools/* (工具定义)
  - src/utils/envUtils.js (环境工具)

[TO] 被消费于:
  - src/coordinator/ (内部使用)
  - src/commands/ (命令实现)
  - src/tools/AgentTool/ (Agent 工具)

[HERE] 位置:
  - src/coordinator/ 位于协调层
  - 管理 Agent 协调行为
```

---

## 核心功能

### 协调器模式 (`coordinatorMode.ts`)

```typescript
// 检查协调器模式是否启用
isCoordinatorMode(): boolean

// 获取允许的工具白名单
getAllowedTools(): string[]

// 检查特性开关
checkFeatureGate(): boolean
```

### 工具白名单
- 异步 Agent 允许的工具
- 同步 Agent 允许的工具
- 特殊模式下的工具限制

### 特性开关
- GrowthBook 集成
- 环境变量覆盖
- A/B 测试支持

---

## 模式类型

1. **标准模式** — 完整工具集
2. **协调器模式** — 有限的工具集，专注于协调
3. **简单模式** — 最小工具集，快速响应

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
