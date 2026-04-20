# 本仓库补充约定（非官方）

本文档仅适用于 `breeze-agent-skills` 仓库，用来补充该仓库对 commit message 的本地格式要求。
这些规则不是 `git-commit` 技能的通用/官方规范，只有在处理本仓库提交时才应采用。

## Commit Body 格式

当提交信息需要正文时，正文使用 `- ` 开头的列表项表达，每行一条完整信息。
不要写成普通段落，也不要混用段落和列表。

推荐形式：

```text
<type>(<scope>): <summary>

- 第一条结果或改动
- 第二条结果或改动
- 第三条结果或改动
```

示例：

```text
chore(monorepo): 通过 catalog 统一剩余硬编码依赖版本

- 使用 codemod 迁移硬编码版本到 catalog
- 新增 pnpm Workspace 与 Catalog 指南文档
- sidebar 注册新文档入口
```

## 使用时机

- 当前仓库为 `breeze-agent-skills`
- 用户明确要求 commit body 使用 `- ` 列表
- 已观察到仓库现有提交明确采用这一格式，并希望延续
