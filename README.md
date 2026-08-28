# 论文阅读工作流

一个面向 Codex 的中文论文阅读 Skill，用于把单篇技术论文整理成有来源依据的结构化笔记，并继续处理公式、图表、指标和术语追问。它也支持从 Zotero 获取论文、更新既有 Notion 数据库条目，以及写入后的回读验收。

## 主要能力

- 生成 `TL;DR + Background + Motivation + Method + Experiments + Drawbacks` 结构的中文论文笔记。
- 区分论文定义、实验直接证据、阅读者推断和尚未验证内容。
- 对公式逐符号解释，区分相近比值、执行阶段、参数快照和 token/序列粒度。
- 安全更新既有 Notion 条目，保留数据库属性，并在异步写入后重新获取页面验收。

## 安装

### 推荐：直接克隆到 Codex Skills 目录

```bash
git clone https://github.com/COK-ZhangZiliang/paper-reading-workflow.git \
  ~/.codex/skills/paper-reading-workflow
```

仓库根目录就是完整 Skill，克隆后无需再复制子目录。若目标目录已经存在，请使用下面的更新命令，不要重复克隆。

以后更新到最新版本：

```bash
git -C ~/.codex/skills/paper-reading-workflow pull --ff-only
```

安装后，在新的 Codex 对话中调用：

```text
使用 $paper-reading-workflow 精读这篇论文，并把中文笔记写入数据库对应项。
```

## 目录结构

```text
paper-reading-workflow/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── full-note-and-evidence.md
    ├── live-publication.md
    └── technical-explanations.md
```

Skill 标识必须使用 ASCII kebab-case，因此内部名称为 `paper-reading-workflow`；界面名称、使用说明和工作流内容均为中文。
