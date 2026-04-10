# Migrations 模块 · 数据迁移

> P2 | src/migrations/ 模块文档

## 模块职责

**Migrations 模块** 实现设置和配置迁移，包括模型别名迁移、权限设置迁移、MCP 配置迁移等。确保用户设置在新版本中保持兼容。

---

## 成员列表

### 模型迁移

| 文件 | 职责 |
|------|------|
| `migrateLegacyOpusToCurrent.ts` | Opus 旧版本迁移 |
| `migrateOpusToOpus1m.ts` | Opus 1M 迁移 |
| `migrateFennecToOpus.ts` | Fennec 到 Opus 迁移 |
| `migrateSonnet1mToSonnet45.ts` | Sonnet 1M 到 4.5 迁移 |
| `migrateSonnet45ToSonnet46.ts` | Sonnet 4.5 到 4.6 迁移 |

### 设置迁移

| 文件 | 职责 |
|------|------|
| `migrateAutoUpdatesToSettings.ts` | 自动更新迁移 |
| `migrateBypassPermissionsAcceptedToSettings.ts` | 权限绕过迁移 |
| `migrateEnableAllProjectMcpServersToSettings.ts` | MCP 服务器迁移 |

### 其他迁移

| 文件 | 职责 |
|------|------|
| `migrateReplBridgeEnabledToRemoteControlAtStartup.ts` | REPL 桥接迁移 |
| `resetAutoModeOptInForDefaultOffer.ts` | 自动模式重置 |
| `resetProToOpusDefault.ts` | Pro 到 Opus 默认重置 |

---

## 依赖关系

```
[FROM] 依赖:
  - src/utils/settings/ (设置管理)
  - src/utils/config.js (配置管理)
  - src/services/analytics/ (分析)
  - src/utils/model/ (模型工具)

[TO] 被消费于:
  - src/setup.ts (应用设置)
  - src/utils/settings/settings.ts (设置加载)

[HERE] 位置:
  - src/migrations/ 位于数据迁移层
  - 确保设置向后兼容
```

---

## 迁移设计模式

```typescript
// 迁移函数模式
export function migrateLegacyOpusToCurrent() {
  // 1. 读取旧设置
  // 2. 转换到新格式
  // 3. 保存新设置
  // 4. 记录迁移事件
}
```

---

## 迁移时机

1. **应用启动时** — 检查并执行迁移
2. **设置加载后** — 应用迁移
3. **版本升级后** — 首次运行迁移

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
