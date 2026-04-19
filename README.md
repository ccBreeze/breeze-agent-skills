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
- [skills 商店](https://skills.sh/)

## 推荐 Skills

### 资源合集

- [anthropics/skills](https://github.com/anthropics/skills)
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)：收集社区中较常见的 Claude skills

### 个人工作流

- [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)：改善 Claude Code 的行为
- [build-with-agent-team](https://github.com/coleam00/context-engineering-intro/blob/main/use-cases/build-with-agent-team/README.md)：多 Agent 协作。
- [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills)

### 设计相关

- [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)
