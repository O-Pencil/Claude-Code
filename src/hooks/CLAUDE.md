# Hooks 模块 · React 钩子库

> P2 | src/hooks/ 模块文档

## 模块职责

**Hooks 模块** 提供 85+ React 钩子，覆盖工具权限、命令绑定、历史记录、通知、UI 交互等。封装可复用的状态逻辑和副作用处理。

---

## 成员列表（按功能分类）

### 工具权限

| 钩子 | 职责 |
|------|------|
| `useCanUseTool.tsx` | 工具可用性检查 |
| `toolPermission/` | 权限处理钩子 |

### 命令和键位

| 钩子 | 职责 |
|------|------|
| `useCommandKeybindings.tsx` | 命令键位绑定 |
| `useCommandQueue.ts` | 命令队列管理 |
| `useArrowKeyHistory.tsx` | 箭头键历史导航 |
| `useCopyOnSelect.ts` | 选中复制 |

### 历史和记忆

| 钩子 | 职责 |
|------|------|
| `useAssistantHistory.ts` | 助手历史 |
| `useFileHistorySnapshotInit.ts` | 文件历史快照 |
| `useMemoryNotifications.ts` | 记忆通知 |

### 通知和提示

| 钩子 | 职责 |
|------|------|
| `useChromeExtensionNotification.tsx` | Chrome 扩展通知 |
| `useClaudeCodeHintRecommendation.tsx` | 提示推荐 |
| `useClipboardImageHint.ts` | 剪贴板图片提示 |
| `fileSuggestions.ts` | 文件建议 |
| `unifiedSuggestions.ts` | 统一建议 |

### UI 交互

| 钩子 | 职责 |
|------|------|
| `useBlink.ts` | 闪烁效果 |
| `useDoublePress.ts` | 双击检测 |
| `useElapsedTime.ts` | 经过时间 |
| `useExitOnCtrlCD.ts` | Ctrl+C 退出 |
| `useDeferredHookMessages.ts` | 延迟消息 |

### 数据和状态

| 钩子 | 职责 |
|------|------|
| `useDiffData.ts` | 差异数据 |
| `useDiffInIDE.ts` | IDE 差异 |
| `useDirectConnect.ts` | 直接连接 |
| `useDynamicConfig.ts` | 动态配置 |

### 认证和 API

| 钩子 | 职责 |
|------|------|
| `useApiKeyVerification.ts` | API 密钥验证 |
| `useCancelRequest.ts` | 取消请求 |

### 背景和任务

| 钩子 | 职责 |
|------|------|
| `useBackgroundTaskNavigation.ts` | 后台任务导航 |
| `useAwaySummary.ts` | 离开摘要 |

### 其他钩子

| 钩子 | 职责 |
|------|------|
| `useAfterFirstRender.ts` | 首次渲染后 |
| `useVerboseOverride.tsx` | 详细模式覆盖 |
| `useIdeSelection.ts` | IDE 选择 |
| `useLastUserMessage.ts` | 最后用户消息 |
| `useMaxThinkingTokens.ts` | 最大思考 Token |
| `useModelOverride.tsx` | 模型覆盖 |
| `useContextCollapse.tsx` | 上下文折叠 |
| `useReactiveCompact.tsx` | 反应式压缩 |
| `useSummarize.ts` | 摘要 |
| `useWorktreeMode.ts` | Worktree 模式 |
| `notifs/` | 通知钩子 |
| `renderPlaceholder.ts` | 占位符渲染 |

---

## 依赖关系

```
[FROM] 依赖:
  - React (useState, useEffect, useContext, etc.)
  - src/state/ (状态管理)
  - src/types/ (类型定义)
  - src/utils/ (工具函数)

[TO] 被消费于:
  - src/components/ (UI 组件)
  - src/entrypoints/ (入口点)
  - src/tools/ (工具实现)

[HERE] 位置:
  - src/hooks/ 位于 UI 逻辑层
  - 连接组件和业务逻辑
```

---

## 钩子设计模式

```typescript
// 状态钩子
export function useStateHook() {
  const [state, setState] = useState(initialState);
  return { state, setState };
}

// 副作用钩子
export function useSideEffect() {
  useEffect(() => {
    // 副作用逻辑
  }, [dependencies]);
}

// 上下文钩子
export function useContextHook() {
  const context = useContext(SomeContext);
  return context;
}
```

---

*P2 文档生成于 2026-04-10 | 使用 oh-my-dev skill*
