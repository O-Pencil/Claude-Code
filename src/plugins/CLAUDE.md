# Plugins 模块 · 插件系统

> P2 | src/plugins/ 模块文档

## 模块职责

**Plugins 模块** 实现插件系统，包括内置插件、捆绑插件、插件加载和注册等。支持扩展应用功能。

---

## 成员列表

| 文件/目录 | 职责 | 行数 |
|-----------|------|------|
| `builtinPlugins.ts` | 内置插件定义 | ~200 行 |
| `bundled/` | 捆绑插件目录 | |

---

## 依赖关系

```
[FROM] 依赖:
  - src/types/plugin.ts (插件类型)
  - src/utils/plugins/ (插件工具)
  - src/services/plugins/ (插件服务)

[TO] 被消费于:
  - src/commands/plugin/ (插件命令)
  - src/setup.ts (初始化)
  - src/services/plugins/ (插件管理)

[HERE] 位置:
  - src/plugins/ 位于插件层
  - 提供可扩展的功能模块
```

---

## 插件架构

```typescript
interface Plugin {
  name: string;
  version: string;
  activate(context: PluginContext): void;
  deactivate(): void;
}
```

---

## 内置插件

- **核心插件** — 基础功能扩展
- **工具插件** — 额外工具支持
- **集成插件** — 第三方服务集成

---

## 插件生命周期

```
1. 发现插件
2. 验证插件
3. 加载插件
4. 激活插件
5. 运行插件
6. 停用插件
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
