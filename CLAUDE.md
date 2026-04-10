# Claude Code 源码研究项目

> P1 | 项目根文档和导航地图

## 项目概述

**Claude Code v2.1.88 反编译源码** — 用于学习/研究 Claude Code 工程实现（代理循环、工具系统、权限体系、MCP 集成、遥测与配置等）。

**语言**: TypeScript  
**类型**: 研究/学习项目（非官方，仅供学习）  
**版本**: 2.1.88

---

## 目录结构

```
Claude-Code/
├── CLAUDE.md          # P1 根文档（本文件）
├── package.json       # 项目配置和构建脚本
├── tsconfig.json      # TypeScript 配置
├── QUICKSTART.md      # 构建和运行说明
├── README.md          # 英文说明
├── README_CN.md       # 中文说明
├── docs/              # 深度分析文档（中英双语）
│   ├── en/            # 英文文档
│   └── zh/            # 中文文档
├── src/               # 源代码（P2 模块见下方链接）
│   ├── bridge/        # 桥接层（VSCode 集成）
│   ├── cli/           # 命令行接口
│   ├── commands/      # 命令实现（80+ 命令）
│   ├── components/    # UI 组件（React/Ink）
│   ├── services/      # 核心服务层
│   ├── tools/         # 工具实现（30+ 工具）
│   ├── skills/        # 技能系统
│   ├── tasks/         # 任务管理
│   ├── types/         # 类型定义
│   └── utils/         # 工具函数
├── tools/             # 外部工具存根
├── stubs/             # 类型存根
├── scripts/           # 构建脚本
└── vendor/            # 第三方依赖
```

---

## P2 模块文档导航

| 模块 | 路径 | 说明 |
|------|------|------|
| **Bridge** | [src/bridge/CLAUDE.md](src/bridge/CLAUDE.md) | VSCode 桥接层，主入口 |
| **CLI** | [src/cli/CLAUDE.md](src/cli/CLAUDE.md) | 命令行接口和传输层 |
| **Commands** | [src/commands/CLAUDE.md](src/commands/CLAUDE.md) | 80+ 内置命令实现 |
| **Components** | [src/components/CLAUDE.md](src/components/CLAUDE.md) | UI 组件库（React/Ink） |
| **Services** | [src/services/CLAUDE.md](src/services/CLAUDE.md) | 核心服务层 |
| **Tools** | [src/tools/CLAUDE.md](src/tools/CLAUDE.md) | 30+ 工具实现 |
| **Skills** | [src/skills/CLAUDE.md](src/skills/CLAUDE.md) | 技能系统 |
| **Tasks** | [src/tasks/CLAUDE.md](src/tasks/CLAUDE.md) | 任务管理和调度 |
| **Types** | [src/types/CLAUDE.md](src/types/CLAUDE.md) | 类型定义和生成代码 |
| **Utils** | [src/utils/CLAUDE.md](src/utils/CLAUDE.md) | 通用工具函数 |

---

## 构建和运行

```bash
# 安装依赖
npm install

# 构建项目
npm run build

# 类型检查
npm run check

# 运行（构建后）
npm start
```

---

## 核心架构

### 分层设计

```
┌─────────────────────────────────────────┐
│           CLI / VSCode Bridge           │  ← 入口层
├─────────────────────────────────────────┤
│              Commands                   │  ← 命令层（80+ 命令）
├─────────────────────────────────────────┤
│    Services     │    Tools    │ Skills  │  ← 核心层
├─────────────────────────────────────────┤
│         Tasks   │   State     │ Types   │  ← 基础层
└─────────────────────────────────────────┘
```

### 关键抽象

1. **Agent Loop** — 代理循环，核心决策引擎
2. **Tool System** — 工具调用和执行框架
3. **Permission System** — 权限审批和沙箱控制
4. **MCP Integration** — Model Context Protocol 集成
5. **Session Management** — 会话状态和历史管理
6. **Bridge API** — VSCode 扩展桥接接口

---

## 配置路径

| 配置 | 路径 | 说明 |
|------|------|------|
| TypeScript | `tsconfig.json` | 编译配置 |
| 项目依赖 | `package.json` | npm 依赖和脚本 |
| 构建脚本 | `scripts/` | prepare-src.mjs, build.mjs |

---

## 代码标准

- **语言**: TypeScript 5.x
- **模块**: ES Modules (`"type": "module"`)
- **目标**: Node.js 18+
- **构建工具**: esbuild + TypeScript
- **代码风格**: 遵循原有项目约定

---

## DIP 协议

本项目使用 **DIP (Dual-phase Isomorphic Documentation)** 协议：

- **P1**: 根文档（本文件），全局拓扑和导航 ✅
- **P2**: 模块文档（每个源目录一个 CLAUDE.md），成员列表和职责 ✅ 10/10 核心模块
- **P3**: 文件头注释（WHO/FROM/TO/HERE），快速相关性判断 ✅ 50+ 核心文件

### DIP 覆盖统计

| 层级 | 目标 | 已完成 | 覆盖率 |
|------|------|--------|--------|
| P1 | 1 文件 | 1 文件 | 100% |
| P2 | 10 核心模块 | 10 模块 | 100% |
| P3 | 50+ 文件 | 50 文件 | 目标达成 |

**P3 覆盖的核心文件包括：**
- 入口点：`cli.tsx`, `setup.ts`, `QueryEngine.ts`
- 核心层：`Tool.ts`, `Task.ts`, `commands.ts`, `tools.ts`, `query.ts`
- 状态管理：`AppState.tsx`, `bootstrap/state.ts`, `context.ts`
- 工具系统：`BashTool.tsx`, `AgentTool.tsx`, `FileEditTool.ts`, `FileReadTool.ts`
- 服务层：`analytics/index.ts`, `api/claude.ts`, `api/logging.ts`, `mcp/client.ts`, `SessionMemory/sessionMemory.ts`
- 桥接层：`bridgeMain.ts`, `replBridge.ts`
- CLI：`print.ts`, `useCanUseTool.tsx`, `useCommandKeybindings.tsx`
- 配置：`config.ts`, `settings/settings.ts`, `model/model.ts`
- 权限：`permissions/permissions.ts`
- 工具函数：`bash/commands.ts`, `git.ts`, `diff.ts`, `forkedAgent.ts`, `claudemd.ts`, `cwd.ts`, `platform.ts`, `execFileNoThrow.ts`
- 组件：`App.tsx`
- 键位：`KeybindingContext.tsx`
- 上下文：`mailbox.tsx`, `ink.ts`
- 常量：`constants/tools.ts`
- 迁移：`migrations/migrateLegacyOpusToCurrent.ts`
- 记忆：`memdir/paths.ts`
- 历史：`history.ts`, `handlePromptSubmit.ts`
- 成本：`cost-tracker.ts`
- 协调器：`coordinator/coordinatorMode.ts`
- 分析：`analytics/index.ts`
- Shell：`shell/shellToolUtils.ts`

---

## 重要声明

> ⚠️ **学习用途**：本项目仅供学习与技术研究使用，**严禁商业用途**。  
> ⚠️ **非官方**：与 Anthropic 无任何隶属/合作/背书关系。  
> ⚠️ **不提供担保**：按"现状"提供，不附带任何保证。

---

*P1 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
