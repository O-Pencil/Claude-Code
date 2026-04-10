# Constants 模块 · 常量定义

> P2 | src/constants/ 模块文档

## 模块职责

**Constants 模块** 定义全项目共享的常量，包括 API 限制、文件类型、错误 ID、OAuth 配置、系统提示、XML 标签等。提供统一的常量管理，避免硬编码。

---

## 成员列表

### API 和限制

| 文件 | 职责 |
|------|------|
| `apiLimits.ts` | API 调用限制 |
| `toolLimits.ts` | 工具使用限制 |

### 文件和路径

| 文件 | 职责 |
|------|------|
| `files.ts` | 文件类型和扩展名 |
| `product.ts` | 产品相关常量 |

### 错误和日志

| 文件 | 职责 |
|------|------|
| `errorIds.ts` | 错误 ID 定义 |
| `messages.ts` | 消息常量 |

### 认证和 OAuth

| 文件 | 职责 |
|------|------|
| `oauth.ts` | OAuth 配置 |
| `keys.ts` | 密钥常量 |

### 系统和提示

| 文件 | 职责 |
|------|------|
| `system.ts` | 系统常量 |
| `prompts.ts` | 提示模板 |
| `systemPromptSections.ts` | 系统提示章节 |

### XML 和格式

| 文件 | 职责 |
|------|------|
| `xml.ts` | XML 标签定义 |
| `outputStyles.ts` | 输出样式 |

### 其他常量

| 文件 | 职责 |
|------|------|
| `common.ts` | 通用常量 |
| `betas.ts` | Beta 功能标志 |
| `figures.ts` | 数字常量 |
| `spinnerVerbs.ts` | 旋转器动词 |
| `turnCompletionVerbs.ts` | 轮次完成动词 |
| `cyberRiskInstruction.ts` | 网络安全指令 |
| `github-app.ts` | GitHub App 配置 |

---

## 依赖关系

```
[FROM] 依赖:
  - 无外部依赖（纯常量定义）

[TO] 被消费于:
  - 全项目所有模块
  - src/tools/, src/services/, src/components/

[HERE] 位置:
  - src/constants/ 位于基础层
  - 被所有上层模块依赖
```

---

## 常量设计规范

```typescript
// 数值常量
export const MAX_RETRIES = 3;

// 字符串常量
export const API_BASE_URL = 'https://api.anthropic.com';

// 枚举式常量
export const FILE_TYPES = ['ts', 'js', 'py'] as const;

// 对象常量
export const ERROR_CODES = {
  NOT_FOUND: 'E404',
  UNAUTHORIZED: 'E401',
} as const;
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
