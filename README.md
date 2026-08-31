# 论文阅读工作流

一个面向 Codex 的中文论文阅读 Skill，用于把单篇技术论文或技术报告整理成有来源依据的结构化笔记，并继续处理公式、图表、指标和术语追问。完整精读默认从 Zotero 获取原始文献，并将笔记同步到对应 Notion 数据库：优先更新匹配条目，没有匹配条目时在该数据库中新建，最后回读验收。

## 主要能力

- 普通论文默认严格使用 `TL;DR + Background + Motivation + Method + Experiments + Drawbacks`；技术报告则使用顶部 `TL;DR`，其后保留报告正文的顶层章节及原有顺序。两种场景都不自行增加论文信息表、目录或参考资料等模块。
- 除章节标题外，笔记正文默认不使用加粗。
- 区分论文定义、实验直接证据、阅读者推断和尚未验证内容。
- 详细解释核心公式的直觉、作用、计算顺序、关键符号、假设和适用边界。
- 将图表证据自然融入它所支持的现有章节，不另设图表解读模块或逐图卡片；除非用户明确要求，否则不截图、不上传、不嵌入图片。
- 默认更新对应 Notion 数据库中的匹配条目；没有匹配时先复搜，再在该数据库中新建条目。数据库或同名条目仍有歧义时先向用户确认，且不在数据库外新建独立页面。

## 安装

### 推荐：直接克隆到 Codex Skills 目录

```bash
git clone https://github.com/COK-ZhangZiliang/paper-reading-workflow.git \
  ~/.codex/skills/paper-reading-workflow
```

仓库根目录就是完整 Skill，克隆后无需再复制子目录。

若目标目录本身就是通过上述命令创建的 Git 克隆，可更新到最新版本：

```bash
git -C ~/.codex/skills/paper-reading-workflow pull --ff-only
```

若目标目录存在但不是该仓库的 Git 克隆，不要直接执行更新命令或覆盖其中内容；请先备份原目录，再选择新的安装目录或重新克隆。

论文阅读和本地笔记生成不依赖在线连接器。从 Zotero 取文或写入 Notion 时，目标机器还需要相应连接器、本地服务与访问权限。

安装后，在新的 Codex 对话中调用：

```text
使用 $paper-reading-workflow 精读这篇论文。
```

完整精读默认同步到对应 Notion 数据库。若只需要聊天回答或本地草稿，请明确说明“仅回答，不写入 Notion”或“只生成本地草稿”。单项公式、术语或图表追问默认只在对话中回答。

精读技术报告时，笔记仍保留顶部 `TL;DR`，但不强行套用固定的五个论文章节。

## 目录结构

```text
paper-reading-workflow/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── full-note-and-evidence.md
    ├── live-publication.md
    └── technical-explanations.md
```

Skill 标识必须使用 ASCII kebab-case，因此内部名称为 `paper-reading-workflow`；界面名称、使用说明和工作流内容均为中文。
