# 命令 Claude Code CLI

## 权限模式

Claude Code CLI 支持多种权限模式，控制是否需要用户确认每次操作。

| 模式 | 效果 |
|------|------|
| `default` | 默认，每次操作需确认 |
| `acceptEdits` | 自动接受编辑，其他仍需确认 |
| `bypassPermissions` | 全部跳过，完全自动 |
| `plan` | 只读模式，不允许任何修改 |

## 设置方式

**启动时指定：**
```bash
claude --bypassPermissions
claude --permission-mode acceptEdits
claude --permission-mode plan
```

**会话内切换：**
```bash
/perms bypassPermissions
/perms acceptEdits
/perms default
```

## 注意事项

- `bypassPermissions` 会跳过所有安全确认，包括 `git push --force`、`rm -rf` 等危险命令
- 适合可控环境/自动化场景，生产环境谨慎使用
- `plan` 模式适合只做代码分析和规划，不允许任何写操作
