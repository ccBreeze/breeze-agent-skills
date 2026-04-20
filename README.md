# breeze-agent-skills

面向前端与 Monorepo 工作流的 Agent Skills 合集，支持 Claude Code 与 Codex。

## Skills

| Skill                  | 描述                                          |
| ---------------------- | --------------------------------------------- |
| `commit`               | 分析暂存区变更，生成符合规范的 commit message |
| `doc-writer`           | 新建与维护 VitePress 文档页面                 |
| `doc-image-maintainer` | 迁移、重命名并清理 Markdown 图片资源          |
| `generate-drawio`      | 根据代码或描述生成 DrawIO 架构流程图          |

## 安装

### Claude Code（通过插件市场）

在 Claude Code 中注册市场：

```bash
/plugin marketplace add ccBreeze/breeze-agent-skills
```

随后从该市场安装插件：

```bash
/plugin install breeze-agent-skills@breeze-agent-skills
```

### Codex

告诉 Codex：

```
Fetch and follow instructions from https://raw.githubusercontent.com/ccBreeze/breeze-agent-skills/main/.codex/INSTALL.md
```

## 目录结构

```
.claude-plugin/
├── marketplace.json   # Claude Code 插件市场清单
└── plugin.json        # Claude Code 插件清单（skills 指向 .agents/skills/）
.codex/
└── INSTALL.md         # Codex 全局安装指引
.agents/
└── skills/
    ├── commit/
    │   └── SKILL.md
    ├── doc-writer/
    │   ├── SKILL.md
    │   ├── agents/
    │   │   └── openai.yaml
    │   └── references/
    │       └── vitepress-docs.md
    ├── doc-image-maintainer/
    │   ├── SKILL.md
    │   └── agents/
    │       └── openai.yaml
    └── generate-drawio/
        └── SKILL.md
```

## Skills 文档

### 入门介绍

- [What are Skills?](https://agentskills.io/what-are-skills)
- [Skills for Claude](https://claude.com/blog/skills)

### 官方资源

- [anthropics/skills](https://github.com/anthropics/skills)：官方 skills 仓库
- [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)：官方 plugins 总目录

### 工作流增强

- [Yeachan-Heo/oh-my-claudecode](https://github.com/Yeachan-Heo/oh-my-claudecode)：多智能体编排系统
- [Yeachan-Heo/oh-my-codex](https://github.com/Yeachan-Heo/oh-my-codex)：Codex 版工作流增强
- [rtk-ai/rtk](https://github.com/rtk-ai/rtk)：节省 token
- [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)：改善 Claude Code 的行为
- [anthropics/claude-plugins-official · claude-md-management](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/claude-md-management/README.md)：维护和改进 CLAUDE.md
- [anthropics/claude-plugins-official · commit-commands](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/commit-commands/README.md)：提交规范与 PR 流程

## 推荐 Skills

按工作流模式组织。

### 头脑风暴 / 需求设计

- [obra/superpowers](https://github.com/obra/superpowers)：头脑风暴 + 子代理
- [anthropics/claude-plugins-official · feature-dev](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/feature-dev/README.md)：特性开发工作流

### 代码质量

- [anthropics/claude-plugins-official · code-simplifier](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/code-simplifier/agents/code-simplifier.md)：代码简化
- [anthropics/claude-plugins-official · code-review](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/code-review/README.md)：代码审查
- [anthropics/claude-plugins-official · pr-review-toolkit](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/pr-review-toolkit/README.md)：PR 审查工具集

### Agent 工具

- [anthropics/claude-plugins-official · skill-creator](https://github.com/anthropics/claude-plugins-official/blob/main/plugins/skill-creator/README.md)：新建 skill 脚手架

### 未用

- [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
- [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)
