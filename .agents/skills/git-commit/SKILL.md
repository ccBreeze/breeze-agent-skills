---
name: git-commit
description: 审查当前仓库改动并生成高质量 Git 提交。用于用户要求提交当前工作、整理 staged 或 unstaged 变更、生成合适 commit message，或在提交前先检查改动范围时使用。
---

# Git Commit

## 目标

基于当前仓库的真实改动生成准确、可追踪的 Git 提交，同时避免误提无关文件。

## 工作流

1. 先确认改动范围

- 查看 `git status --short`、`git diff --stat`、`git diff --cached --stat`。
- 在写提交信息前，先读懂关键 diff，确认这次提交真正解决了什么问题。
- 如果仓库里混有无关改动，不要擅自一起提交；先缩小到当前任务相关文件，或明确说明需要用户确认。

2. 处理 staged 与 unstaged

- 如果用户明确要求“提交当前工作”，优先提交当前任务相关的改动。
- 若已经有 staged 变更，先确认 staged 内容是否就是预期提交范围。
- 若需要补充 staging，只添加当前任务相关文件；不要顺手纳入看起来不相关的改动。

3. 生成提交信息

- 优先沿用仓库现有提交风格；如果仓库没有明显约定，默认使用简洁的 Conventional Commit 风格。
- 常用前缀包括：`feat`、`fix`、`refactor`、`docs`、`test`、`chore`、`build`。
- 标题聚焦“这次改动带来的结果”，避免只罗列文件名或写成模糊描述。
- 如有必要，可补充 1 到 3 条简短正文，说明背景、关键实现或风险。
- 如果当前仓库存在额外的 commit message 约定，按需读取相应 reference（例如 `breeze-agent-skills` 仓库中的 [references/local-conventions.md](references/local-conventions.md)），并在最终提交信息中遵循该约定。

4. 执行提交

- 使用非交互命令完成提交。
- 不要在未获明确允许时使用 `--amend`、`--no-verify` 或改写历史的操作。
- 如果没有可提交内容，直接说明，不要制造空提交。

5. 返回结果

- 汇总本次提交的主题、影响范围和最终 commit hash。
- 如果因为无关改动、冲突或空 diff 而没有提交，明确说明原因与下一步建议。
